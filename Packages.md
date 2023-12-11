#Golang #Packages

<font style="font-size: 50px">&#xeb29</font>

[Go](Go.md)

---

### Import packages
<br>

this line of code import the `fmt` package

```go
import "fmt"


```
<br>

**Importing multiple packages at the same statement**
```go
// use two import statements
import "fmt"
import "math"

// use single import statement
import (
  "fmt"
  "math"
)
```
<br>

### Commonly used packages
<br>

+ [`fmt`](fmt%20package.md)
+ [`math`](math%20package.md)
+ [`strings`](strings%20package.md)
<br>


### Custom Package
<br>

1. We need to create a new file and declare the package name at the top
```go
// declare package
package calculator
```
2. Now, we can code inside the file in order to create functions which are going to be contained in the package you named
```go
package calculator

// create add function
func Add(n1, n2 int) int {
  return n1 + n2
}

// create subtract function
func Subtract(n1, n2 int) int {
  return n1 - n2
}
```
>[!note]
>This file doesn't contain the main package. Hence, the Go compiler doesn't consider this as an executable program and it is created for the sole purpose of sharing and reusing.

3. Importing custom package
So, now you can import your custom package to the main file
```go
package main 

// import the custom package calculator
import (
  "fmt"
  "Packages/calculator"
)

func main() {

  number1 := 9
  number2 := 5

  // use the add function of calculator package
  fmt.Println(calculator.Add(number1, number2))

  // use the subtract function of calculator package
  fmt.Println(calculator.Subtract(number1, number2))

}
```

>[!note]
>We have used `Packages/calculator` as the name of the package. This is because the calculator package is present inside the `Packages` folder and we are providing the path to that package from the location of the `main` file.

>[!question]
>How to create a dir system in for programming and managing my own packages

