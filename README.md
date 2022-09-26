<div align="center">

  <h1><code>NEAR ABI</code></h1>

  <p>
    <strong>ABI schema format and tooling to define interface to NEAR smart contracts.</strong>
  </p>
</div>

❗ **Warning: Format and tooling has not been finalized, should only be used for testing/experimentation**

> What is an ABI?

An ABI (Application Binary Interface) traditionally defines the interface between two binary program modules. In the context of the NEAR ABI, this JSON schema defines the interface to the Wasm binary (smart contract) on the NEAR network, including parameter and result formats used through the NEAR runtime.

> Why do we need ABI?

- Human-readable format to easy indicate how to interact with the contract
- Standard interface definition cross-language
  - Ability to be used with any combination of contract SDK and client libraries
- Tooling built using the ABI to be able to generate code to interact with any contract easily

## Usage
Ensure you have [cargo-near](https://github.com/near/cargo-near/edit/main/README.md) installed

To generate an ABI for a contract within the directory containing contract's Cargo.toml

```console
$ cargo near abi
```

## Supported tools:

### ABI generation

- [near-sdk-rs](https://github.com/near/near-sdk-rs) (version `4.1.0-pre.3` and above) and [cargo-near](https://github.com/near/cargo-near): `cargo-near` is a [cargo](https://doc.rust-lang.org/cargo/) extention that is used to build the contract and generate the ABI from a `near-sdk-rs` contract.

> Note: This is currently WIP and unstable. Stable released versions and examples to come.

### ABI clients
- [near-abi-client-rs](https://github.com/near/near-abi-client-rs): Generates glue code to interact with contracts through RPC using [workspaces-rs](https://github.com/near/workspaces-rs).
- [near-abi-client-js](https://github.com/near/near-abi-client-js): Generates JS glue code to interact with contracts through RPC using [near-api-js](https://github.com/near/near-api-js).
- [near-sdk-abi](https://github.com/near/near-sdk-abi): Generates [near-sdk-rs](https://github.com/near/near-sdk-rs) glue code to make cross-contract calls within other contracts.

### Utility Libraries
- [near-abi-rs](https://github.com/near/near-abi-rs): Common Rust types used across Rust ABI crates.
