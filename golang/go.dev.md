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

