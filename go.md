# Go

## Create new module

```bash
echo 'layout go' > .envrc
direnv allow
go mod init example/user/module
```

## Example program

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, world.")
}
```

## Common commands

Build:

```go build```

Install program:

```go install example/user/module```
