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

```bash
go mod edit --replace example.com/greetings=../greetings
go mod tidy
```