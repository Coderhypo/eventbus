# eventbus

Lightweight eventbus for golang

## Usage

### Static topic

```go
package main

import (
	"fmt"
	"github.com/hyponet/eventbus/bus"
)

func aAndBComputer(a, b int) {
	fmt.Printf("%d + %d = %d\n", a, b, a+b)
}

func main() {
	_, _ = bus.Register("op.int.and", aAndBComputer)
	bus.Publish("op.int.and", 1, 2)
}
```

### Wildcard topic

```go
package main

import (
	"fmt"
	"github.com/hyponet/eventbus/bus"
)

func bobDoSomething() {
	fmt.Println("Bob do something")
}

func aliceDoSomething() {
	fmt.Println("Alice do something")
}

func main() {
	_, _ = bus.Register("partner.bob.do", bobDoSomething)
	_, _ = bus.Register("partner.alice.do", aliceDoSomething)
	bus.Publish("partner.*.do")
}
```