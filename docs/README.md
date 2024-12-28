# Language Guides

## Rust Guide

1.  Ensure Rust and Cargo are installed in the container (handled by the devcontainer).
2.  Install `tonic` and `prost` (gRPC and protobuf crates): Add these to `Cargo.toml`.
3.  Generate Rust code from the proto file:
    ```bash
    protoc --proto_path=proto proto/service.proto \
        --rust_out=src/proto \
        --tonic_out=src/proto
    ```
4. Create a `src/server.rs` and `src/client.rs` file.
5. Create a `Cargo.toml` file in the root of the project.
6. Create a `src/main.rs` file.
7. Build and run the project: `cargo run`

**Example `Cargo.toml`:**

```toml
[package]
name = "grpc-example"
version = "0.1.0"
edition = "2021"

[dependencies]
tonic = "0.10"
prost = "0.11"
tokio = { version = "1", features = ["full"] }
async-trait = "0.1"

[build-dependencies]
tonic-build = "0.10"
```
