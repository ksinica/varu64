# varu64 

[![Go Reference](https://pkg.go.dev/badge/github.com/ksinica/varu64.svg)](https://pkg.go.dev/github.com/ksinica/varu64)

`varu64` provides Go implementation of [VarU64](https://github.com/AljoschaMeyer/varu64).
```go
package main

import (
	"encoding/json"
	"os"

	"github.com/ksinica/varu64"
)

func main() {
	type foo struct {
		Bar varu64.Uint64 `json:"bar"`
	}
	json.NewEncoder(os.Stdout).Encode(&foo{
		Bar: varu64.U64(72057594037927933),
	})
	// {"bar": "fefffffffffffffd"}

	var val varu64.Uint64
	val.SetValue(1)
	json.NewEncoder(os.Stdout).Encode(&val)
	// "01"
}
```
## License

Source code is available under the MIT [License](/LICENSE).