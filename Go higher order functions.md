#Golang #Functions #HiherOrderFunction

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---

A Higher-Order function is a function that receives a function as an argument or returns the function as output.

Passing functions as arguments
```go
package main

import "fmt"

func sum(x, y int) int {
	return x + y
}
func partialSum(x int) func(int) int {
	return func(y int) int {
		return sum(x, y)
	}
}
func main() {
	partial := partialSum(3)
	fmt.Println(partial(7))
}
```
==output==
```
10
```


Retuning function from other one
```go
package main

import "fmt"

func squareSum(x int) func(int) func(int) int {
	return func(y int) func(int) int {
		return func(z int) int {
			return x*x + y*y + z*z
		}
	}
}
func main() {
	// 5*5 + 6*6 + 7*7
	fmt.Println(squareSum(5)(6)(7))
}
```
==output==
```
110
```