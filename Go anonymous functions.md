#Golang #Functions #AnonymousFunction

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---

An anonymous function is a function that was declared without any named identifier to refer to it. Anonymous functions can accept inputs and return outputs, just as standard functions do.

```go
package main

import "fmt"

var (
	area = func(l int, b int) int {
		return l * b
	}
)

func main() {
	fmt.Println(area(20, 30))
}
```

Passing arguments to an anonymous function
```go
package main

import "fmt"

func main() {
	func(l int, b int) {
		fmt.Println(l * b)
	}(20, 30)
}
```


Function defined to accept a parameter and return value.
```go
package main

import "fmt"

func main() {
	fmt.Printf(
		"100 (°F) = %.2f (°C)\n",
		func(f float64) float64 {
			return (f - 32.0) * (5.0 / 9.0)
		}(100),
	)
}
```