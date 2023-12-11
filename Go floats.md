#Golang #DataTypes #Numeric #Float

[Go back](Data%20Types.md#Three%20basic%20data%20types)

---

For storing positive and negative numbers with a decimal point ---> $\mathbb{R}$

#### Go keywords for floats

|Type|Size|Range|
|---|---|---|
|`float32`|32 bits|-3.4e+38 to 3.4e+38.|
|`float64`|64 bits|-1.7e+308 to +1.7e+308.|

>[!tip]
>The default type for float is `float64`. If you do not specify a type, the type will be `float64`.


**float32 keyword**
```go
package main  
import ("fmt")  
  
func main() {  
  var x float32 = 123.78  
  var y float32 = 3.4e+38  
  fmt.Printf("Type: %T, value: %v\n", x, x)  
  fmt.Printf("Type: %T, value: %v", y, y)  
}
```

<br>

**float64 keyword**
```go
package main  
import ("fmt")  
  
func main() {  
  var x float64 = 1.7e+308  
  fmt.Printf("Type: %T, value: %v", x, x)  
}
```

