#Golang #DataStrcutures #Arrays
<br>

`ris:FileList` `ris:CodeBox`

[Go](Go.md)

---

The statement structure for declaring an array is basically `var myArray [size]int`, with size as the number of elements the array can store
<br>
==example==
```go
var numbers [10]int
numbers[0] = 1
numbers[1] = 2
//...
```
<br>

You can set the values in one line statement
<br>
```go
myArray := [3]char{'a', 'b', 'c'}

```

Or
```go
myArray := [...]int{1,2,3}
```


<br>

>[!question]
>What methods or functions can I use on an array?


#### The ``len`` function

You can get the length of an array by calling the `len` function and passing argument (an array) to it
```go
var myArray [3]int = [3]int{1,2,3}
fmt.Printf("Length is %v", len(myArray))
```


#### Array of arrays
```go
var matrix [3][3]int = [3][3]int{ [3]int{1,2,3}, [3]int{4,5,6}, [3]int{7,8,9} }
fmt.Prinln(matrix)
```

#### Arrays pointers
When an array `a` is defined, and then you declare another variable `b` that is initialised as `b = a`, the value in `b`  is just a copy of the `a` one, but not a pointer. So for point to `a`, you have to initialise `b` as a pointer to `a` like this
`b = &a`


