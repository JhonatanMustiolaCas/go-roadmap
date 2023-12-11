#Golang #DataTypes #Numeric

[Go back](Data%20Types.md#Three%20basic%20data%20types)

---

Go has differents numeric data types:

* [Integers](Go%20integers.md)
* [Floats](Go%20floats.md)
* Complex


**Some useful examples**
```go
package main

import (
    "fmt"
    "math/bits"
    "reflect"
    "unsafe"
)

func main() {
    //This is computed as const uintSize = 32 << (^uint(0) >> 32 & 1) // 32 or 64
    sizeOfIntInBits := bits.UintSize
    fmt.Printf("%d bits\n", sizeOfIntInBits)
    
    var a int
    fmt.Printf("%d bytes\n", unsafe.Sizeof(a))
    fmt.Printf("a's type is %s\n", reflect.TypeOf(a))
    
    b := 2
    fmt.Printf("b's typs is %s\n", reflect.TypeOf(b))
}
```
**Output:**
```
64 bits
8 bytes
a's type is int
b's typs is int
```
