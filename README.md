# Duktape bindings for Go(Golang) [![wercker status](https://app.wercker.com/status/8f7563013d2fcf2390b014762c2d5100/s/master "wercker status")](https://app.wercker.com/project/bykey/8f7563013d2fcf2390b014762c2d5100)
[Duktape](http://duktape.org/index.html) is a thin, embeddable javascript engine.
Most of the [api](http://duktape.org/api.html) is implemented.
The exceptions are listed [here](https://github.com/olebedev/go-duktape/blob/master/api.go#L1294).

### Usage
```go
package main

import "fmt"
import "github.com/olebedev/go-duktape"

func main() {
  ctx := duktape.NewContext()
  ctx.EvalString(`2 + 3`)
  result = ctx.GetNumber(-1)
  ctx.Pop()
  fmt.Println("result is:", result)
}
```

### Go specific notes

Bindings between Go and Javascript contexts are not fully functional.
However, binding a Go function to the Javascript context is available:
```go
package main

import "fmt"
import "github.com/olebedev/go-duktape"

func main() {
  ctx := duktape.NewContext()
  ctx.PushGofunc("log", func(ctx *duktape.Context) int {
    fmt.Println("Go lang Go!")
    return 0
  })
  ctx.EvalString(`log()`)
}
```
than run it.
```bash
$ go run
$ Go lang Go!
```

### Status

The package is not fully tested, so be careful.


### Contribution

Pull requests are welcome!
