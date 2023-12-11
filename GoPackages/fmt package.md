#Golang #Package

[Packages](Packages.md#Commonly%20used%20packages)

---

In Go, the `fmt` package provides functions to format our input/output data. For example, the `fmt.Println()` function prints the data to the output screen.

<br>
Some of the functions are:

| Functions   | Descriptions                                                   |
| ----------- | -------------------------------------------------------------- |
| `Print()`   | prints the text to output screen                               |
| `Println()` | prints the text to output with a new line character at the end |
| `Printf()`  | prints the formatted string to the output screen               |
| `Scan()`    | get input values from the user                                 |
| `Scanf()`   | get input values using the format specifier                    |
| `Scanln()`  | get input values until the new line is detected                |
<br>


==Example==
```go
package main
import "fmt"

func main() {

  var number int

  // take input value
  fmt.Scan(&number)

  // print using Println
  fmt.Println("Number is", number)

  fmt.Print("Using Print")
  fmt.Println("Using Println")

}
```
<br>

==example==
```go
package main
import "fmt"

func main() {

  var number int
  
  fmt.Scanf("%d", &number)  // Input: 10
  fmt.Printf("%d", number)  // Output: 10

}
```

In the above example, functions

- `fmt.Scanf("%d", &number)` - takes integer input value and assign it to the `number` variable
- `fmt.Printf("%d", number)` - replaces the `%d` format specifier by the value of `number` and prints it