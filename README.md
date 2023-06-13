# Osmosis

Osmosis employs **CosmWasm** as its Virtual Machine (VM), which means that WebAssembly (Wasm) smart contracts can be deployed to the Osmosis blockchain.

## CosmWasm

CosmWasm is a smart contract module designed for blockchains built with the Cosmos SDK. It allows developers to write smart contracts using the Rust programming language. A typical CosmWasm project is divided into 5 main files:

- `contract.rs`: Contains the actual logic of the smart contract.
- `error.rs`: Defines the error types that the smart contract can return.
- `state.rs`: Represents the state of the smart contract.
- `lib.rs`: Adheres to standard Rust practices, and is used to define all the modules.
- `msg.rs`: Defines the messages that can be sent to the smart contract. Messages are the primary means of interaction with contracts, allowing for actions such as token transfers and invoking contract functions.

Generally, CosmWasm smart contracts consist of three primary functions:

1. `instantiate`: Similar to a constructor in Solidity, this function is called during the instantiation of the contract.
2. `execute`: Called when interacting with the contract. Typically performs a match on the message type to determine the action to be taken.
3. `query`: Used to query the contract state and retrieve information.

To make a function callable from outside the contract, it must be annotated with an attribute:

```rust
#[cfg_attr(not(feature = "library"), entry_point)]
```
This attribute designates the function as an entry point to the contract.

Entry functions require several arguments, including:
 - Deps, DepsMut, or OwnedDeps: Holds all the external dependencies of the contract.
 - Env: Contains environment variables.
 - MessageInfo: Includes information such as the sender's address and tokens being sent.
 - ExecuteMessage, QueryMessage, or InstantiateMessage: Depending on which entry point function is being called, this argument specifies which message should be called.

 ## Resources

1. [CosmWasm Book](https://book.cosmwasm.com/index.html)
2. [CosmWasm Examples](https://github.com/deus-labs/cw-contracts)
3. [CosmWasm Template](https://github.com/CosmWasm/cw-template)
4. [CosmWasm Zero to Hero (YouTube)](https://www.youtube.com/watch?v=ocR-1FvIQD8)
5. CosmWasm Rust API:
   - [CosmWasm STD](https://docs.rs/cosmwasm-std/1.2.6/cosmwasm_std/)
   - [CosmWasm Storage Plus](https://docs.rs/cw-storage-plus/1.0.1/cw_storage_plus/)
   - [CosmWasm Multi Test](https://docs.rs/cw-storage-plus/1.0.1/cw_storage_plus/)
   - [CosmWasm Utils](https://docs.rs/cw-storage-plus/1.0.1/cw_storage_plus/)
6. [Awesome CosmWasm](https://github.com/CosmWasm/awesome-cosmwasm)

