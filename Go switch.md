#Golang #Syntax #Switch

[Go](Go.md)

---

It starts with the `switch` keyword followed by an expression for comparing it to a series of possible cases that we considered
```go
switch i {
	case 0: fmt.Println("Zero")
	case 1: fmt.Println("One")
	case 2: fmt.Println("Two")
	case 3: fmt.Println("Three")
	case 4: fmt.Println("Four")
	case 5: fmt.Println("Five")
	default: fmt.Println("Unknown Number")
}
```

>[!info]
>The `break` statement isn't necessary for killing the `switch`

You can add more possible values per `case`
```go
switch j {
	case "hola", "buen dia", "como estas": ftm.Println("Es un saludo")
	case "chao", "adios", "hasta luego": ftm.Println("Es una despedida")
	case 1,2,3,4: ftm.Println("Es un matematico")
}
```

if you want the switch cases evaluation to continue, you have to insert the
`fallthrough` statement
```go
i := 10
switch {
	case i <= 10:
		fmt.Println("Less than or equal to ten")
		fallthrough
	case i <= 20:
		fmt.Println("Less than or equal to twenty")
	default:
		fmt.Println("Greater than twenty")
}
```


Working with type cases
```go
var i interface{} = 1
switch i.(type) {
	case int:
		fmt.Println("i is an int")
		break
		fmt.Println("This will print too") //it won't be printed actually, because of the break statement just above
	case string:
		//...
	default:
		//...
}
```

