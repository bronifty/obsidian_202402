https://go.dev/doc/tutorial/call-module-code

greetings/

```bash
go mod init example.com/greetings
```

```go

package greetings

import "fmt"

func Hello(name string) string {
	message := fmt.Sprintf("Hi, %w. Welcome!", name)
	return message
}

```

hello/

```bash
go mod init example.com/hello
```

```go
package main

import (
"fmt"
"example.com/greetings"
)

func main() {
message := greetings.Hello("Brother Nifty")
fmt.Println(message)
}
```

- go mod edit --replace the namespace with the local module
```bash
go mod edit --replace example.com/greetings=../greetings
go mod tidy
go run . 
```

- let's add some error handling
```go
package greetings

import (
	"errors"
	"fmt"
)

func Hello(name string) (string, error) {
	if name == "" {
		return "", errors.New("empty name")
	}
	message := fmt.Sprintf("Hi, %v. Welcome!", name)
	return message, nil
}
```

```go
package main

import (
	"fmt"
	"log"

	"example.com/greetings"
)

func main() {
	log.SetPrefix("greetings: ")
	log.SetFlags(0)

	message, err := greetings.Hello("ffej")
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(message)
}


```