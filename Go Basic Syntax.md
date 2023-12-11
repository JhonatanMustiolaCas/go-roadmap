#Syntax #Basics #Golang #Completed

`ris:Code` `ris:CodeBox`

[Go](Go.md)

---
#### About Go

It was created by ==Robert Griesemar==, ==Rob Pike== and ==Ken Thompson== as an alternative to the three more used languages in Google Corporation:
1. python &#xe73c  Easy to use, but slow
2. Java &#xe738  Increasingly complex to use type system
3. C/C++ Complex type system and slow compile times

*What defines Go?*
* Strong and statically typed
* Excellent community
* Key features
	* Simplicity
	* Fast compile times
	* Garbage collected
	* Built-in concurrency
	* Compile to standalone binaries
* Paradigms
	* imperative
	* OPP
	* Functional

>[!note]
>Furthermore, Go is created by inspiration from Pascal, Modula and Oberon, and its syntax is similar to C


>[!info]
>Visit the go web site for more info [click here](https://golang.org)or you can also go to the Golang Bridge community web site [here](https://golangbridge.org)

##### tags:
#HardTyped #GarbageCollecting #FastCompile #Simplicity #ConcurrentProgramming

---

#### Cracking on the first steps

Adding the first line of code which every .go file must has into
```go
1|package main
2|...
```

`package` is a ==keyword== that defines which code bundle a .go file belongs to. In this case, to the `main` package. ==There must be only a== package per folder, and each .go file must has the same declaration at the first line, as above
The `main` package is the *entry point* of the program.

For obtaining arguments through the entry point
```go
import (
	"fmt"
	"os"
)
fun main(){
	if len(os.Args) != 2 {
		os.Exit(1)
	}
	ftm.Println("It's over", os.Args[1])
}
```

<br>

Printing "Hello, World"
```go
1|package main
2|import "fmt"
3|func main() {
4|    fmt.Println("Hello, World")
5| }
6|
```
the `import` statement is used for importing external packages which are going to be used in the code
>[!warning]-
>If you import a package that you don't use in any part of the program, then the compiler won't let the code to be compiled

**For running and compiling this code**
`go run hello.go` runs the code, printing
```
Hello, World
```
on the terminal

`go build hello.go` compiles the code as executable file: `.exe, .sh` and others depending on your OS
<br>

Taking a input and printing it
```go
1|package main
2|import "fmt"
3|func main() {
4|    fmt.Println("Enter your name: ")
5|    var name string
6|    fmt.Scanln(&name)
7|    fmt.Printf("Hi, %s! I'm Go", name)
8| }
9|
```
---


#### Operators

* **Arithmetical**

| symbol |                    description                     | example  |
|:------:|:--------------------------------------------------:|:--------:|
|   +    |                sum between operands                | x + y... |
|   -    |    subtract the right operand from the left one    |  x - y   |
|   *    |               multiply the operands                |  x * y   |
|   /    | Divide the left operand according to the right one |  x / y   |
|   %    |      Give the rest or module from a division       |  x %  y  |

* **Comparative**

| symbol |         description          | example |
|:------:|:----------------------------:|:-------:|
|   ==   |   if two values are equals   | x == y  |
|   !=   | if two values are differents | x != y  |
|   <    |          less than           |  x < y  |
|   >    |         greater than         |  x > y  |
|   <=   |      less or equal than      | x <= y  |
|   >=   |    greater or equal than     | x >= y  |


* **Logic**

|      symbol      | description |       example        |
|:----------------:|:-----------:|:--------------------:|
|        &&        |     and     |        x && y        |
| &#10072;&#10072; |     or      | x &#10072;&#10072; y |
|        !         |     not     |          !x          |


* **Assignment**

| symbol |                              description                              |   example   |
|:------:|:---------------------------------------------------------------------:|:-----------:|
|   =    |                     assign a value to a variable                      | x = "value" |
|   +=   |   sum a value to a variable and assign the result at the same time    |   x += 1    |
|   -=   | subtract a value to a variable and assign the result at the same time |   x -= 1    |
| &#42;= | multiply a value to a variable and assign the result at the same time | y &#42;= 2  |
|   /=   |  divide a value to a variable and assign the result at the same time  |   x /= 2    |
|   %=   |  divide a value to a variable and assign the module at the same time  |   x %= 2    |


* **Bits**

|  symbol  |                                description                                 |   example    |
|:--------:|:--------------------------------------------------------------------------:|:------------:|
|    &     |              return the bits established in the two variables              |    x & y     |
| &#10072; |            return the bits established in at least one variable            | x &#10072; y |
|    ^     |         return the bits established in one variable but not both ones         |    x ^ y     |
|    <<    | move the bits of a value to left according to a indicated position numbers |    x << 2    |
|    >>    |                        same as above, but to right                         |    x >> 2    |
|    ^     |                     for inverting the bits of a value                      |      &#94;x      |


#### Examples with operators

```go
//...
	//Bitwise operators

	a := 10 //1010
	b := 3  //0011
	fmt.Println(a & b)  //0010
	fmt.Println(a | b)  //1011
	fmt.Println(a ^ b)  //1001
	fmt.Println(a & ^b) // 1010 & 1100 = 1000
	
	f := 8 //this is equivalent to 2^3
	g := 16 //this is equivalent to 2^4
	fmt.Println(f << 3) // 2^3 * 2^3 = 64
	fmt.Println(g << 3) // 2^4 * 2^3 = 128
	fmt.Println(f >> 3) // 2^3 / 2^3 = 1
	fmt.Println(g >> 3) // 2^4 / 2^3 = 2
```



##### tags:
#Operators