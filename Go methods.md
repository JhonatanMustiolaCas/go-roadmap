#Golang #Functions 

[Go back](Go%20functions.md#Other%20types%20of%20functions)

---
Just as functions, but for adding functionality to structs
```go
func main() {
	g := greeter{
		greeting: "Hello",
		name: "Go"
	}
	g.greet()
}
type greeter struct {
	greeting string
	name string
}
//method definition
func (g greeter) greet() {
	fmt.Println(g.greeting, g.name)
}
```

if you pass a pointer to a struct, then you can change the field values
```go
func main() {
	g := greeter{
		greeting: "Hello",
		name: "Go"
	}
	g.greet()
	fmt.Println("The new name is: ", g.name)
	//output - > The new name is: 
}
type greeter struct {
	greeting string
	name string
}
//method definition
func (g *greeter) greet() {
	fmt.Println(g.greeting, g.name)
	g.name = ""
}
```