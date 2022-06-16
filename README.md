## hlm ipfs-cluster golang sdk

### 使用说明
#### 导入go.mod
```go
go 1.17

require (
	hlm-ipfs/ipfs-clutser-go-sdk v0.0.0-00010101000000-000000000000
)
replace hlm-ipfs/ipfs-clutser-go-sdk => github.com/hlm-ipfs/ipfs-clutser-go-sdk v0.0.0-20220525063417-c84e0e0342cf
```

```go
import (
	"context"
	"fmt"
	"github.com/ipfs/go-cid"
	"github.com/ipfs/ipfs-cluster/api"
	sdk "hlm-ipfs/ipfs-clutser-go-sdk/sdk/client"
)
func main()  {
	cl, err := sdk.NewDefaultClient(&sdk.Config{
		Host:     "10.41.1.3",
		Port:     "9094",
		AccessKey: "017194e9718f07feefc4b03422d8be5df654bafc623251480f7d760d1209b4ca39",
		SecretKey: "02595d553697305c7670dfd92628e5ff68080335265edf804aea4e6e8df5112464",
	})
	if err != nil {
		panic(err)
	}
	id,err:=cl.ID(context.TODO())
	if err != nil {
		panic(err)
	}
	fmt.Println(id)
	hash, err := cid.Decode("QmZCLMSHcVfFjYFzwTd4Nq9EUto2zzY6U6SPBU7DypGhzs")
	if err != nil {
		panic(err)
	}
	pinOut,err:=cl.Pin(context.TODO(),api.NewCid(hash),api.PinOptions{})
	if err != nil {
		panic(err)
	}
	fmt.Println(pinOut)
}
```

### api文档
[https://hlm-ipfs.github.io/ipfs-clutser-go-sdk/#/](https://hlm-ipfs.github.io/ipfs-clutser-go-sdk/#/)
