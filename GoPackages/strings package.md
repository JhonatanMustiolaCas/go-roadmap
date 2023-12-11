#Golang #Package 
<br>
[Packages](Packages.md#Commonly%20used%20packages)

---

The `strings` package provides functions to perform operations on UTF-8 encoded strings. For example, `strings.Contains()` checks if the string contains a substring.
<br>

Some of the commonly used `strings` functions:
<br>

|Functions|Descriptions|
|---|---|
|`Compare()`|checks if two strings are equal|
|`Contains()`|checks if the string contains a substring|
|`Count()`|counts the number of times a substring present in the string|
|`Join()`|creates a new string by concatenating elements of a string array|
|`ToLower()`|converts the string to lowercase|
|`ToUpper()`|converts the string to uppercase|

<br>

==Example==
```go
package main

// import multiple packages
import (
  "fmt"
  "strings"
  )

func main() {

  // convert the string to lowercase
  lower := strings.ToLower("GOLANG STRINGS")
  fmt.Println(lower)

  // convert the string to uppercase
  upper := strings.ToUpper("golang strings")
  fmt.Println(upper)

  // create a string array
  stringArray := []string{"I love", "Go Programming"}

  // join elements of array with space in between
  joinedString := strings.Join(stringArray, " ");
  fmt.Println(joinedString)

}
```
==output==
```terminal
golang strings
GOLANG STRINGS
I love Go Programming
```