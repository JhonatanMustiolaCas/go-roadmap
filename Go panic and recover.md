#Golang #GoPanic #GoRecover

[Go](Go.md)

---

### Panic
Occur when program cannot continue at all

* Function will top executions
	* Deferred functions will still fire
* If nothing handles panic, program will exit


### Recover
* Used to recover from panics
* Only useful in deferred functions
* Current function will not attempt to continue, but higher functions in call stack will


```go
import (
	"fmt"
	"log"
)

func main() {
	fmt.Println("start")
	panicker()
	fmt.Println("end")
}

func panicker() {
	fmt.Println("About to panic")
	defer func(){
		if err := recover(); err != nil {
			log.Println("Error: ", err)
			panic(err) //just if error is no recognised
		}
	}()
}
```