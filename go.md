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

## Lambda

### Simple Lambda

```go
package main

import (
        "fmt"
        "context"
        "github.com/aws/aws-lambda-go/lambda"
)

type MyEvent struct {
        Name string `json:"name"`
}

func HandleRequest(ctx context.Context, name MyEvent) (string, error) {
        return fmt.Sprintf("Hello %s!", name.Name ), nil
}

func main() {
        lambda.Start(HandleRequest)
}
```

### Structured types

```go
package main
 
import (
        "fmt"
        "github.com/aws/aws-lambda-go/lambda"
)

type MyEvent struct {
        Name string `json:"What is your name?"`
        Age int     `json:"How old are you?"`
}
 
type MyResponse struct {
        Message string `json:"Answer:"`
}
 
func HandleLambdaEvent(event MyEvent) (MyResponse, error) {
        return MyResponse{Message: fmt.Sprintf("%s is %d years old!", event.Name, event.Age)}, nil
}
 
func main() {
        lambda.Start(HandleLambdaEvent)
}
```

## Environment variables

```go
package main

import (
    "fmt"
    "os"
    "github.com/aws/aws-lambda-go/lambda"
)

func main() {
    fmt.Printf("%s is %s. years old\n", os.Getenv("NAME"), os.Getenv("AGE"))

}
```

### Global state

```go
package main
 
import (
        "log"
        "github.com/aws/aws-lambda-go/lambda"
        "github.com/aws/aws-sdk-go/aws/session"
        "github.com/aws/aws-sdk-go/service/s3"
        "github.com/aws/aws-sdk-go/aws"
)
 
var invokeCount = 0
var myObjects []*s3.Object
func init() {
        svc := s3.New(session.New())
        input := &s3.ListObjectsV2Input{
                Bucket: aws.String("examplebucket"),
        }
        result, _ := svc.ListObjectsV2(input)
        myObjects = result.Contents
}
 
func LambdaHandler() (int, error) {
        invokeCount = invokeCount + 1
        log.Print(myObjects)
        return invokeCount, nil
}
 
func main() {
        lambda.Start(LambdaHandler)
}
```

### Errors

```go
package main
 
import (
        "errors"
        "github.com/aws/aws-lambda-go/lambda"
)
 
func OnlyErrors() error {
        return errors.New("something went wrong!")
}
 
func main() {
        lambda.Start(OnlyErrors)
}
```

## Common commands

Build:

```go build```

Install program:

```go install example/user/module```
