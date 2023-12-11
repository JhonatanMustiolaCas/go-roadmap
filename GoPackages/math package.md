#Golang #Package 
<br>
[Packages](Packages.md#Commonly%20used%20packages)

---

The `math` package provides various functions to perform mathematical operations. For example, `math.Sqrt()` finds the square root of a number.
<br>

Some of the commonly used `math` functions:
<br>

|Functions|Descriptions|
|---|---|
|`Sqrt()`|returns the square root of the number|
|`Cbrt()`|returns the cube root of the number|
|`Max()`|returns the larger number between two|
|`Min()`|returns the smaller number between two|
|`Mod()`|computes the remainder after division|

<br>

==Example==
```go
package main
import "fmt"

// import the math package
import "math"

func main() {

  // find the square root
  fmt.Println(math.Sqrt(25))    // 5

  // find the cube root
  fmt.Println(math.Cbrt(27))    // 3

  // find the maximum number
  fmt.Println(math.Max(21, 18))    // 21

  // find the minimum number
  fmt.Println(math.Min(21, 18))    // 18

  // find the remainder
  fmt.Println(math.Mod(5, 2))    // 1

}
```