#Golang #defer

[Go](Go.md)

---

It allows to defer a function till surrounding ones might has been executed.
==syntax==
```go
//...
defer fmt.Println("Hola")
//...
```

### Rules

1. _A deferred function’s arguments are evaluated when the defer statement is evaluated_
```go
func a() {
    i := 0
    defer fmt.Println(i)
    i++
    return
}
//print 0
```

2. _Deferred function calls are executed in Last In First Out order after the surrounding function returns_
```go
func b() {
    for i := 0; i < 4; i++ {
        defer fmt.Print(i)
    }
}
```

3. _Deferred functions may read and assign to the returning function’s named return values_
```go
func c() (i int) {
    defer func() { i++ }()
    return 1
}
```

>[!tip]
>This is convenient for modifying the error return value of a function; we will see an example of this shortly.


### How to use defer

for example, in this case we defer two functions. Due to `defer` is designed according to ==LIFO== algorithm, so the returned values of the deferred functions will be obtained in reversed order in comparison to the order we implemented them on code
```go
func main() {
    defer fmt.Println("Goodbye") 
    defer fmt.Println("Hello World")
}
```
output:
```
Hello World
Goodbye
```

`defer` is mostly used to stablish final functions to be executed in order to close or clean up what was done from the surrounding functions.
For example, close a file
```go
func main() {
    src, err := os.Open(srcName)
    if err != nil {
    	log.Fatal(err)
    }
    defer src.Close()

    dst, err := os.Create(dstName)
    if err != nil {
        log.Fatal(err)
    }
    defer dst.Close()

    written, err = io.Copy(dst, src)
    if err != nil {
        log.Fatal(err)
    }
}
```


For measure the runtime of a program
```go
func(w http.ResponseWriter, r *http.Request) {
	t := time.Now()
	defer func() {
		log.Println(time.Since(t)
	})
 
    // middleware code   
}
```





>[!danger]
>defer a `nil` executes panic
