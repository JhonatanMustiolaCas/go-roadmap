#Golang #GoErrors

[Go](Go.md)

---

Errors in Go are treated as functions which return values (error values or type error)

Errors are an implementation of an interface, like this
```go
type error interface {
    Error() string
}
```
It just return a string with an error message

### Constructing errors

By errors package's unexported `errorString` type
```go
// errorString is a trivial implementation of error.
type errorString struct {
    s string
}

func (e *errorString) Error() string {
    return e.s
}
```


Errors can be constructed on the fly using Go’s built-in `errors` or `fmt` packages. For example, the following function uses the `errors` package to return a new error with a static error message:
```go
package main

import "errors"

func DoSomething() error {
    return errors.New("something didn't work")
}
```

Similarly, the `fmt` package can be used to add dynamic data to the error, such as an `int`, `string`, or another `error`. For example:
```go
package main

import "fmt"

func Divide(a, b int) (int, error) {
    if b == 0 {
        return 0, fmt.Errorf("can't divide '%d' by zero", a)
    }
    return a / b, nil
}
```

>[!note]
>Note that `fmt.Errorf` will prove extremely useful when used to wrap another error with the `%w` format verb


- Errors can be returned as `nil`, and in fact, it’s the default, or “zero”, value of on error in Go. This is important since checking `if err != nil` is the idiomatic way to determine if an error was encountered (replacing the `try`/`catch` statements you may be familiar with in other programming languages).
   
- Errors are typically returned as the last argument in a function. Hence in our example above, we return an `int` and an `error`, in that order.
   
- When we do return an error, the other arguments returned by the function are typically returned as their default “zero” value. A user of a function may expect that if a non-nil error is returned, then the other arguments returned are not relevant.
   
- Lastly, error messages are usually written in lower-case and don’t end in punctuation. Exceptions can be made though, for example when including a proper noun, a function name that begins with a capital letter, etc.

### Defining Expected Errors[](https://earthly.dev/blog/golang-errors/#defining-expected-errors)

Another important technique in Go is defining expected Errors so they can be checked for explicitly in other parts of the code. This becomes useful when you need to execute a different branch of code if a certain kind of error is encountered.

#### Defining Sentinel Errors[](https://earthly.dev/blog/golang-errors/#defining-sentinel-errors)

Building on the `Divide` function from earlier, we can improve the error signaling by pre-defining a “Sentinel” error. Calling functions can explicitly check for this error using `errors.Is`:
```go
package main

import (
    "errors"
    "fmt"
)

var ErrDivideByZero = errors.New("divide by zero")

func Divide(a, b int) (int, error) {
    if b == 0 {
        return 0, ErrDivideByZero
    }
    return a / b, nil
}

func main() {
    a, b := 10, 0
    result, err := Divide(a, b)
    if err != nil {
        switch {
        case errors.Is(err, ErrDivideByZero):
            fmt.Println("divide by zero error")
        default:
            fmt.Printf("unexpected division error: %s\n", err)
        }
        return
    }

    fmt.Printf("%d / %d = %d\n", a, b, result)
}
```


#### Defining Custom Error Types[](https://earthly.dev/blog/golang-errors/#defining-custom-error-types)

Many error-handling use cases can be covered using the strategy above, however, there can be times when you might want a little more functionality. Perhaps you want an error to carry additional data fields, or maybe the error’s message should populate itself with dynamic values when it’s printed.

You can do that in Go by implementing custom errors type.

Below is a slight rework of the previous example. Notice the new type `DivisionError`, which implements the `Error` `interface`. We can make use of `errors.As` to check and convert from a standard error to our more specific `DivisionError`.
```go
package main

import (
    "errors"
    "fmt"
)

type DivisionError struct {
    IntA int
    IntB int
    Msg  string
}

func (e *DivisionError) Error() string { 
    return e.Msg
}

func Divide(a, b int) (int, error) {
    if b == 0 {
        return 0, &DivisionError{
            Msg: fmt.Sprintf("cannot divide '%d' by zero", a),
            IntA: a, IntB: b,
        }
    }
    return a / b, nil
}

func main() {
    a, b := 10, 0
    result, err := Divide(a, b)
    if err != nil {
        var divErr *DivisionError
        switch {
        case errors.As(err, &divErr):
            fmt.Printf("%d / %d is not mathematically valid: %s\n",
              divErr.IntA, divErr.IntB, divErr.Error())
        default:
            fmt.Printf("unexpected division error: %s\n", err)
        }
        return
    }

    fmt.Printf("%d / %d = %d\n", a, b, result)
}
```


### Errors Are Better Wrapped[](https://earthly.dev/blog/golang-errors/#errors-are-better-wrapped)

The snippet below is refactored so that is uses `fmt.Errorf` with a `%w` verb to “wrap” errors as they “bubble up” through the other function calls. This adds the context needed so that it’s possible to deduce which of those database operations failed in the previous example.
```go
package main

import (
    "errors"
    "fmt"

    "example.com/fake/users/db"
)

func FindUser(username string) (*db.User, error) {
    u, err := db.Find(username)
    if err != nil {
        return nil, fmt.Errorf("FindUser: failed executing db query: %w", err)
    }
    return u, nil
}

func SetUserAge(u *db.User, age int) error {
    if err := db.SetAge(u, age); err != nil {
      return fmt.Errorf("SetUserAge: failed executing db update: %w", err)
    }
}

func FindAndSetUserAge(username string, age int) error {
  var user *User
  var err error

  user, err = FindUser(username)
  if err != nil {
      return fmt.Errorf("FindAndSetUserAge: %w", err)
  }

  if err = SetUserAge(user, age); err != nil {
      return fmt.Errorf("FindAndSetUserAge: %w", err)
  }

  return nil
}

func main() {
    if err := FindAndSetUserAge("bob@example.com", 21); err != nil {
        fmt.Println("failed finding or updating user: %s", err)
        return
    }

    fmt.Println("successfully updated user's age")
}
```