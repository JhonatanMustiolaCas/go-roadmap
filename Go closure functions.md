#Golang #Functions #ClosureFUnction

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---

Closures are a special case of anonymous functions. Closures are anonymous functions which access the variables defined outside the body of the function.

Anonymous function accessing the variable defined outside body.
```go
package main

import "fmt"

func main() {
	l := 20
	b := 30

	func() {
		var area int
		area = l * b
		fmt.Println(area)
	}()
}
```


Anonymous function accessing variable on each iteration of loop inside function body.
```go
package main

import "fmt"

func main() {
	for i := 10.0; i < 100; i += 10.0 {
		rad := func() float64 {
			return i * 39.370
		}()
		fmt.Printf("%.2f Meter = %.2f Inch\n", i, rad)
	}
}
```