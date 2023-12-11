#Golang #Functions #VariadicFunctions

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---

### Variadic functions

A variadic function is a function that accepts a variable number of arguments. In Golang, it is possible to pass a varying number of arguments of the same type as referenced in the function signature. To declare a variadic function, the type of the final parameter is preceded by an ellipsis, "...", which shows that the function may be called with any number of arguments of this type. This type of function is useful when you don't know the number of arguments you are passing to the function, the best example is built-in Println function of the fmt package which is a variadic function.

```go
package main

import "fmt"

func main() {
	variadicExample("red", "blue", "green", "yellow")
}

func variadicExample(s ...string) {
	fmt.Println(s[0])
	fmt.Println(s[3])
}
```
==output==
```
red
yellow
```

```go
package main

import "fmt"

func main() {
	
	variadicExample()
	variadicExample("red", "blue")
	variadicExample("red", "blue", "green")
	variadicExample("red", "blue", "green", "yellow")
}

func variadicExample(s ...string) {
	fmt.Println(s)
}
```
==output==
```
[]
[red blue]
[red blue green]
[red blue green yellow]
```



```go
package main

import "fmt"

func main() {
	fmt.Println(calculation("Rectangle", 20, 30))
	fmt.Println(calculation("Square", 20))
}

func calculation(str string, y ...int) int {

	area := 1

	for _, val := range y {
		if str == "Rectangle" {
			area *= val
		} else if str == "Square" {
			area = val * val
		}
	}
	return area
}
```
==output==
```go
600
400
```

In the following example, the function signature accepts an arbitrary number of arguments of type ``slice``.
```go
package main

import (
	"fmt"
	"reflect"
)

func main() {
	variadicExample(1, "red", true, 10.5, []string{"foo", "bar", "baz"},
		map[string]int{"apple": 23, "tomato": 13})
}

func variadicExample(i ...interface{}) {
	for _, v := range i {
		fmt.Println(v, "--", reflect.ValueOf(v).Kind())
	}
}
```
==output==
```
1 -- int
red -- string
true -- bool
10.5 -- float64
[foo bar baz] -- slice
map[apple:23 tomato:13] -- map
```
