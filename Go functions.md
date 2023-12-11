#Golang #Functions

[Go](Go.md)

---

The single most popular Go function is **main()**, which is used in every independent Go program
```go
package main

func main() {
	//code
}
```
<br>

### Creating a function in Go
1. Declare the `func` keyword
2. Name the function
3. Add a pair of parenthesis bounded to the name
4. Then create a block containing the code of the function

==Example==
```go
package main

import "fmt"

// SimpleFunction prints a message
func SimpleFunction() {
	fmt.Println("Hello World")
}

func main() {
	SimpleFunction()
}
```
<br>

### A function with parameters
When passing information through arguments, you have to add them into the parenthesis just right next of the function name.
==Example==
```go
package main

import "fmt"

// Function accepting arguments
func add(x int, y int) {
	total := 0
	total = x + y
	fmt.Println(total)
}

func main() {
	// Passing arguments
	add(20, 30)
}
```

>[!question] investigate this
>If the functions with names that start with an uppercase letter will be exported to other packages. If the function name starts with a lowercase letter, it won't be exported to other packages, but you can call this function within the same package.


### Functions that return value

It is required a ``return`` statement
==Example==
```go
package main

import "fmt"

// Function with int as return type
func add(x int, y int) int {
	total := 0
	total = x + y
	return total
}

func main() {
	// Accepting return value in varaible
	sum := add(20, 30)
	fmt.Println(sum)
}
```

>[!warning]
>The types of input and return value must match with function signature. If we will modify the above program and pass some string value in argument then program will throw an exception "cannot use "test" (type string) as type int in argument to add".



### Named return values

It is possible to name a return value. When doing that, you can omit the variable name in the return statement, like this
```go
package main

import "fmt"

func rectangle(l int, b int) (area int) {
	var parameter int
	parameter = 2 * (l + b)
	fmt.Println("Parameter: ", parameter)

	area = l * b
	return // Return statement without specify variable name
}

func main() {
	fmt.Println("Area: ", rectangle(20, 30))
}
```

>[!note]
>Since the function is declared to return a value of type int, the last logical statement in the execution flow must be a return statement that returns a value of the declared type.



### Returning Multiple Values
Specifying multiple return values
```go
package main

import "fmt"

func rectangle(l int, b int) (area int, parameter int) {
	parameter = 2 * (l + b)
	area = l * b
	return // Return statement without specify variable name
}

func main() {
	var a, p int
	a, p = rectangle(20, 30)
	fmt.Println("Area:", a)
	fmt.Println("Parameter:", p)
}
```

>[!question]
>Is it possible to define multiple return values of diferent types?



### Passing address to a function
Passing the address of variable to the function and the value of a variables modified using dereferencing inside body of function
```go
package main

import "fmt"

func update(a *int, t *string) {
	*a = *a + 5      // defrencing pointer address
	*t = *t + " Doe" // defrencing pointer address
	return
}

func main() {
	var age = 20
	var text = "John"
	fmt.Println("Before:", text, age)

	update(&age, &text)

	fmt.Println("After :", text, age)
}
```
<br>

### Returning errors
```go
func main() {
	d, err = divide(5.0, 0.0)
	if err != nil{
		fmt.Println(err)
		return
	}
	fmt.Println(d)
}

func divide(a,b float64) (float64, error) {
	if b == 0.0 {
		return 0.0, fmt.Errorf("cannot divide by zero")
	}
	return a/b, nil
}
```


### Functions into variables
```go
func main() {
	var divide func(float64, float64) (float64, error)
	divide = func divide(a,b float64) (float64, error) {
		if b == 0.0 {
			return 0.0, fmt.Errorf("cannot divide by zero")
		}else {
			return a/b, nil
		}
	}
	d, err = divide(5.0, 0.0)
	if err != nil{
		fmt.Println(err)
		return
	}
	fmt.Println(d)
}



```
<br>

### Naming conventions

- A name must begin with a letter, and can have any number of additional letters and numbers.
- A function name cannot start with a number.
- A function name cannot contain spaces.
- If the functions with names that start with an uppercase letter will be exported to other packages. If the function name starts with a lowercase letter, it won't be exported to other packages, but you can call this function within the same package.
- If a name consists of multiple words, each word after the first should be capitalized like this: empName, EmpAddress, etc.
- function names are case-sensitive (car, Car and CAR are three different variables).


### Other types of functions

+ [Anonymous functions](Go%20anonymous%20functions.md)
+ [Closure functions](Go%20closure%20functions.md)
+ [Higher order functions](Go%20higher%20order%20functions.md)
+ [User defined function types](Go%20user%20defined%20function%20types.md)
+ [Variadic functions](Go%20variadic%20functions.md)
+ [Methods](Go%20methods.md)
