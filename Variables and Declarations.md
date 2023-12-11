#Basics #Syntax #Declarations #Golang #InProgress 

`ris:Links` `ris:CodeS`

[Go](Go.md)

---

#### The `var` statement

It declares a list of variables of a type specified at last
```go
var myvariable string;
var done, inprogress, nostarted bool;
```

You can declare the variable into the package scope as well as the main function scope as the example below
```go
package main
import 'fmt'
var myglobalvar string

func main() {
	var number int;
	//...
}
```
<br>

#### Initialising a variable

A var declaration can include initialisers. Just right one per variable
```go
var hello string = "Hola";
```

But you can also omit the type declaration when you initialise a variable, like this
```go
var hello = "Hello";
```

>[!note]
>This characteristic is called ==Type inference==. You can know more about by clicking [here](https://en.wikipedia.org/wiki/Type_inference)

**You can also omit the `var` statement, but only inside a function scope**
```go
package main

import "fmt"

func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}
```
as above, the `k := 3` declaration replaces `var ... int`

#### Unassigned variables

If any initial value given, then it'll be given zero values to them
* for `int` variables: 0
* for `bool` variables: false
* for `string` variables: "" (empty string)
```go
package main

import "fmt"

func main() {
	var i int
	var f float64
	var b bool
	var s string
	fmt.Printf("%v %v %v %q\n", i, f, b, s)
}
```
Output:
```
0 0 false ""
```
<br>

#### Multivariable Declarations
```go
var a, b, c string = "a", "b", "c";
// or --> var a, b, c = "a", "b", "c";
d, e, f := "d", "e", "f";
```

<br>

#### In block declaration
```go
var (
	a int;
	num int = 1;
	hello string = "hello";
)
```

<br>

#### Shadowing variables

You can redeclare a variable inside a function if the declared one exits outside of it

```go
package main

import "fmt"

var i int = 27

func main() {
	fmt.Println(i) //This output 27
	var i int = 43
	fmt.Println(i) //This output 43
}
```

<br>

#### Go variable naming rules:

- A variable name must start with a letter or an underscore character (_)
- A variable name cannot start with a digit
- A variable name can only contain alpha-numeric characters and underscores (`a-z, A-Z`, `0-9`, and `_` )
- Variable names are case-sensitive (age, Age and AGE are three different variables)
- There is no limit on the length of the variable name
- A variable name cannot contain spaces
- The variable name cannot be any Go keywords
<br>

#### Links

[For knowing about constants in Go](Constants.md)