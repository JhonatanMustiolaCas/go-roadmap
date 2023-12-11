#Golang #Syntax #Looping

[Go](Go.md)

---

Go only has a loop statement: the `for` loop, which has three components

| 1. init statement | 2. condition expession | 3. post statement |
| ----------------- | ---------------------- | ----------------- |
| `for i := 0 `     | `i < 10`               | `i++`             |

components must be divided by semicolon, like this
```go
package main

import "fmt"

func main() {
	sum := 0
	for i := 0; i < 10; i++ {
		sum += i
	}
	fmt.Println(sum)
}
```

The init and post statements are optional
```go
package main

import "fmt"

func main() {
	sum := 1
	for ; sum < 1000; {
		sum += sum
	}
	fmt.Println(sum)
}
```

According to the example above, we can omit the init and post, so we can create a while loop with `for loop` syntax, like this
```go
package main

import "fmt"

func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```

And, further, we can code a infinite loop
```go
package main

func main{
	for {
	}
}
```

You can break any targeted loop in a nested loop
```go
Loop:
for i := 1; i<=3; i++ {
	for j := 1; j<=3; j++ {
		fmt.Println(i * j)
		if i * j >= 3 {
			break Loop
		}
	}
}
```

Looping through collections
```go
s := []int{1, 2, 3}
for k, v := range s {
	fmt.Println(k,v) //k: index, v: value
}
```