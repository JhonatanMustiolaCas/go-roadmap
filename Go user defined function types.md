#Golang #Functions #UserDefinedFunctionType

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---

Golang also support to define our own function types

```go
package main

import "fmt"

type First func(int) int
type Second func(int) First

func squareSum(x int) Second {
	return func(y int) First {
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