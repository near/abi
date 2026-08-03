<div align="center">

  <h1><code>NEAR ABI</code></h1>

  <p>
    <strong>ABI schema format and tooling to define interface to NEAR smart contracts.</strong>
  </p>
</div>

⚠️ **Warning: Format and tooling are not final and changes are likely to happen.**

> What is an ABI?

An ABI (Application Binary Interface) traditionally defines the interface between two binary program modules. In the context of the NEAR ABI, this JSON schema defines the interface to the Wasm binary (smart contract) on the NEAR network, including parameter and result formats used through the NEAR runtime.

> Why do we need ABI?

- Human-readable format to easy indicate how to interact with the contract
- Standard interface definition cross-language
  - Ability to be used with any combination of contract SDK and client libraries
- Tooling built using the ABI to be able to generate code to interact with any contract easily

## Usage

### Rust
Ensure you have [cargo-near](https://github.com/near/cargo-near) installed

To generate an ABI for a contract within the directory containing contract's Cargo.toml

```console
$ cargo near abi
```

Ensure that the project you are generating an ABI for depends on a version of `near-sdk` of `4.1.0` or later and has the `abi` feature enabled.

```toml
near-sdk = { version = "4.1.0", features = ["abi"] }
```

### TypeScript
Ensure you have a [near-sdk-js](https://github.com/near/near-sdk-js) (version 0.7.0 or later) contract

To generate an ABI for a contract within the directory containing contract's package.json

```console
$ npx near-sdk-js build --generateABI path/to/contract.ts
```

The ABI will be put in `build/contract-abi.json`

## Supported tools:

### ABI generation
- [near-sdk-rs](https://github.com/near/near-sdk-rs) (version `4.1.0` and above) and [cargo-near](https://github.com/near/cargo-near) (version `0.3.0` and above): `cargo-near` is a [cargo](https://doc.rust-lang.org/cargo/) extention that is used to build the contract and generate the ABI from a `near-sdk-rs` contract.
- [near-sdk-js](https://github.com/near/near-sdk-js) (version `0.7.0` and above): invoke `near-sdk-js build` with `--generateABI` to generate the ABI from a TypeScript contract (pure JavaScript is not supported yet).

### ABI clients
- [near-abi-client-rs](https://github.com/near/near-abi-client-rs): Generates glue code to interact with contracts through RPC using [workspaces-rs](https://github.com/near/workspaces-rs).
- [near-sdk-abi](https://github.com/near/near-sdk-abi): Generates [near-sdk-rs](https://github.com/near/near-sdk-rs) glue code to make cross-contract calls within other contracts.
- [near-api-js](https://github.com/near/near-api-js): integration with NAJ is coming soon, stay tuned.

### Utility Libraries
- [near2ts](https://github.com/SurgeCode/near2ts): Generate typescript types from ABI `npx near2ts devhub.near`
- [near-abi-rs](https://github.com/near/near-abi-rs): Common Rust types used across Rust ABI crates.
- [near-abi-js](https://github.com/near/near-abi-js): Common types used across JavaScript ABI libraries.
