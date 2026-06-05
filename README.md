[update-readmes]   Mode: rewrite — migrating to template structure...
# evmole

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/evmole)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/evmole.git
cd evmole
```

## Usage

### JavaScript
[API documentation](./javascript/#api) and [usage examples](./javascript#usage) (node, vite, webpack, parcel, esbuild)
```sh
$ npm i evmole
```
```javascript
import { contractInfo } from 'evmole'

const code = '0x6080604052348015600e575f80fd5b50600436106030575f3560e01c80632125b65b146034578063b69ef8a8146044575b5f80fd5b6044603f3660046046565b505050565b005b5f805f606084860312156057575f80fd5b833563ffffffff811681146069575f80fd5b925060208401356001600160a01b03811681146083575f80fd5b915060408401356001600160e01b0381168114609d575f80fd5b80915050925092509256'

console.log( contractInfo(code, {selectors:true, arguments:true, stateMutability:true}) )
// {
//   functions: [
//     {
//       selector: '2125b65b',
//       bytecodeOffset: 52,
//       arguments: 'uint32,address,uint224',
//       stateMutability: 'pure'
//     },
//     ...
```

### Rust
Documentation is available on [docs.rs](https://docs.rs/evmole/latest/evmole/)
```rust
let code = hex::decode("6080604052348015600e575f80fd5b50600436106030575f3560e01c80632125b65b146034578063b69ef8a8146044575b5f80fd5b6044603f3660046046565b505050565b005b5f805f606084860312156057575f80fd5b833563ffffffff811681146069575f80fd5b925060208401356001600160a01b03811681146083575f80fd5b915060408401356001600160e01b0381168114609d575f80fd5b80915050925092509256").unwrap();

println!("{:?}", evmole::contract_info(
    evmole::ContractInfoArgs::new(&code)
        .with_selectors()
        .with_arguments()
        .with_state_mutability()
    )
);
// Contract {
//     functions: Some([
//         Function {
//             selector: [33, 37, 182, 91],
//             bytecode_offset: 52,
//             arguments: Some([Uint(32), Address, Uint(224)]),
//             state_mutability: Some(Pure)
//         },
//         ...
```

### Python
[API documentation](./python/#api)
```sh
$ pip install evmole --upgrade
```
```python
from evmole import contract_info

code = '0x6080604052348015600e575f80fd5b50600436106030575f3560e01c80632125b65b146034578063b69ef8a8146044575b5f80fd5b6044603f3660046046565b505050565b005b5f805f606084860312156057575f80fd5b833563ffffffff811681146069575f80fd5b925060208401356001600160a01b03811681146083575f80fd5b915060408401356001600160e01b0381168114609d575f80fd5b80915050925092509256'

print( contract_info(code, selectors=True, arguments=True, state_mutability=True) )
# Contract(
#     functions=[
#     Function(
#             selector=2125b65b,
#             bytecode_offset=52,
#             arguments=uint32,address,uint224,
#             state_mutability=pure),
#     ...
```

### Go
[API documentation](./go/#api-reference)
```sh
$ go get github.com/cdump/evmole/go
```
```go
package main

import (
    "context"
    "encoding/hex"
    "fmt"

    "github.com/cdump/evmole/go"
)

func main() {
    code, _ := hex.DecodeString("6080604052348015600e575f80fd5b50600436106030575f3560e01c80632125b65b146034578063b69ef8a8146044575b5f80fd5b6044603f3660046046565b505050565b005b5f805f606084860312156057575f80fd5b833563ffffffff811681146069575f80fd5b925060208401356001600160a01b03811681146083575f80fd5b915060408401356001600160e01b0381168114609d575f80fd5b80915050925092509256")

    info, _ := evmole.ContractInfo(context.Background(), code, evmole.Options{
        Selectors:       true,
        Arguments:       true,
        StateMutability: true,
    })

    for _, fn := range info.Functions {
        fmt.Printf("%s: %s @ %d\n", fn.Selector, *fn.Arguments, fn.BytecodeOffset)
    }
    // 2125b65b: uint32,address,uint224 @ 52
    // b69ef8a8:  @ 68
}
```

### Foundry
<a href="https://getfoundry.sh/">Foundry's cast</a> uses the Rust implementation of EVMole
```sh

$ cast selectors $(cast code 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2)
0x06fdde03                           view
0x095ea7b3  address,uint256          nonpayable
0x18160ddd                           view
0x23b872dd  address,address,uint256  nonpayable
...

$ cast selectors --resolve $(cast code 0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2)
0x06fdde03                           view        name()
0x095ea7b3  address,uint256          nonpayable  approve(address,uint256)
0x18160ddd                           view        totalSupply()
0x23b872dd  address,address,uint256  nonpayable  transferFrom(address,address,uint256)
...
```

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/evmole`](https://github.com/Interested-Deving-1896/evmole) and mirrored through:

```
Interested-Deving-1896/evmole  ──►  OpenOS-Project-OSP/evmole  ──►  OpenOS-Project-Ecosystem-OOC/evmole
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[MIT](https://github.com/Interested-Deving-1896/evmole/blob/master/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
