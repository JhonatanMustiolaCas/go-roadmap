#Golang #Numeric #Complex 

[Go numeric](Go%20numeric.md)

---

Defining a complex variable

```go
//implicitly
complexN := 1 + 2i

//explicitly
var complexN complex64 = complex(2, 3)
```

#### Two types of complexes

1. complex64 : *real* 32bits and *imaginary* 32bits
2. complex128 : *real* 64bits and *imaginary* 64bits

#### Operations

Subtracting the real part and the imaginary part
```go
var complexN complex64 = complex(2, 6)
fmt.Printf("real = %v, imaginary = %v", real(complexN), imag(complexN))
```