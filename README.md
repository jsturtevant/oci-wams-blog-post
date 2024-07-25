# OCI Wasm

This repo contains the sample code for the blog post

## Build

```bash
cargo component build --release
cp ./target/wasm32-wasip1/release/hello_wasi_http.wasm service.wasm
```

## Run

```bash
wasmtime serve service.wasm --addr 127.0.0.1:3000
```

```bash
curl http://127.0.0.1:3000
```

## Push to GHCR

Create a Personal Access Token (PAT) with `read:packages` and `write:packages` permissions.

```bash
export CR_PAT=your_github_pat
echo $CR_PAT | docker login ghcr.io -u <your_github_username> --password-stdin

wkg wkg oci push ghcr.io/<your_github_username>/hello-wasi-http:latest service.wasm
```

## Deploy to Kubernetes

```bash
```