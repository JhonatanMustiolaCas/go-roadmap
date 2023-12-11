#Golang #DataTypes #bool 

---

A boolean data type can only be `true` or `false`
The default value of a boolean data type is `false`

```go
package main  
import ("fmt")  
  
func main() {  
  var b1 bool = true _// typed declaration with initial value_  
  var b2 = true _// untyped declaration with initial value_  
  var b3 bool _// typed declaration without initial value_  
  b4 := true _// untyped declaration with initial value_  
  
  fmt.Println(b1) _// Returns true_  
  fmt.Println(b2) _// Returns true_  
  fmt.Println(b3) _// Returns false_  
  fmt.Println(b4) _// Returns true_  
}
```