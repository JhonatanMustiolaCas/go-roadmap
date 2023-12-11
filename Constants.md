#Golang #Constants

[Go back](Variables%20and%20Declarations.md)

---
Use `const` instead of `var`
```go
const Pi = 3.14;
```
*They can be string, character, boolean or numeric values*
>[!warning]
>Constants cannot be declared using the `:=` syntax

- Constant names follow the same naming rules as [variables](https://www.w3schools.com/go/go_variable_naming_rules.php)
- Constant names are usually written in uppercase letters (for easy identification and differentiation from variables)
- Constants can be declared both inside and outside of a function

#### Multiple Constants Declaration

Multiple constants can be grouped together into a block for readability:

```go
package main  
import ("fmt")  
  
const (  
  A int = 1  
  B = 3.14  
  C = "Hi!"  
)  
  
func main() {  
  fmt.Println(A)  
  fmt.Println(B)  
  fmt.Println(C)  
}
```
<br>

#### Arbitrary-precision arithmetic

[Wikipedia: Arbitrary-precision arithmetic](https://en.wikipedia.org/wiki/Arbitrary-precision_arithmetic)
[Go by Example Constants](https://gobyexample.com/constants)
[GoDev: constants](https://go.dev/blog/constants)


### Numeric Constants

Numeric constants are high-precision _values_.

An untyped constant takes the type needed by its context.

Try printing `needInt(Big)` too.

(An `int` can store at maximum a 64-bit integer, and sometimes less.)

```go
import "fmt"

const (
	// Create a huge number by shifting a 1 bit left 100 places.
	// In other words, the binary number that is 1 followed by 100 zeroes.
	Big = 1 << 100
	// Shift it right again 99 places, so we end up with 1<<1, or 2.
	Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
	fmt.Println(needInt(Small))
	fmt.Println(needFloat(Small))
	fmt.Println(needFloat(Big))
}
```

```
21
0.2
1.2676506002282295e+29
```


#### Constants can be used with other numbers like this
```go
const num = 32
var num2 int16 = 2
fmt.Printf("SUM IS %v", num + num2) //in this case, the compiler just substitute the constant identifier to its value. Then the operation is 32 + num2.
```


#### iota
For defining set of related constants values
```go
const (
	_ = iota //0 is descarted
	KB = 1 << (10 * iota)
	MB
	GB
	TB
	PB
	EB
	ZB
	YB
)
```


#### Example by defining a set of roles for users

```go
const (
	idAdmin = 1 << iota
	isHeadQuarters
	canSeeFinancials

	canSeeAfrica
	canSeeAsia
	canSeeEurope
	canSeeNorthAmerica
	canSeeSouthAmerica
)

func main() {
	var userRoles byte = isAdmin | canSeeFinancials | canSeeEurope
	fmt.Printf("%b\n", roles)
	fmt.Printf("is Admin? %v\n", isAdmin & userRoles == isAdmin) //true
}
```