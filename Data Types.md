#Golang #InProgress #DataTypes

`ris:CodeBox`

[Go back](Go.md#Learn%20the%20basics)

---

>[!note]
>A data type specifies the ==size== and type of variables values

### Three basic data types

* [bool](Go%20booleans.md)
* [Numeric](Go%20numeric.md): [integers](Go%20integers.md), [floats](Go%20floats.md), complex
* [string](Go%20string.md)

```go
package main  
import ("fmt")  
  
func main() {  
  var a bool = true     _// Boolean_  
  var b int = 5         _// Integer_  
  var c float32 = 3.14  _// Floating point number_  
  var d string = "Hi!"  _// String_  
  
  fmt.Println("Boolean: ", a)  
  fmt.Println("Integer: ", b)  
  fmt.Println("Float:   ", c)  
  fmt.Println("String:  ", d)  
}
```
<br>

### Type conversions

The expression `T(v)` converts the value `v` to the type `T`.

Some numeric conversions:

var i int = 42
var f float64 = float64(i)
var u uint = uint(f)

Or, put more simply:

i := 42
f := float64(i)
u := uint(f)

Unlike in C, in Go assignment between items of different type requires an explicit conversion. Try removing the `float64` or `uint` conversions in the example and see what happens.