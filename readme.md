# DA Spammer

A tiny Rust CLI tool to **spam blobs + metadata transactions** to an [Avail](https://www.availproject.org/) node.  
It connects to a running Avail RPC endpoint, prepares blobs of a chosen size, computes their commitments, and submits them as signed extrinsics using one of the dev accounts.

---

## ✨ Features

- Connects to an Avail node via RPC (default: `http://127.0.0.1:8546`)
- Supports standard dev accounts (`Alice`, `Bob`, `Charlie`, `Dave`, `Eve`, `Ferdie`, `One`, `Two`)
- Configurable:
  - **Payload size** (1–32 MiB, default: 32)
  - **Number of transactions** (1–100, default: 50)
  - **Blob content character** (default: first letter of the chosen account)
- Precomputes all commitments before submission
- Rotates `app_id` values (like in your example: `i % 5`)
- Logs progress for each transaction

---

## ⚡ Requirements

- Rust (>= 1.70 recommended)
- A running Avail node exposing HTTP RPC at the endpoint you plan to use  
  (for local testing: `http://127.0.0.1:8546`)

---

## 🔧 Build

Clone this repository (or copy the provided source files), then build:

```bash
cargo build --release
```

## 🚀 Run

### Full explicit command

```bash
./target/release/da-spammer \
  --account alice \
  --size-mb 16 \
  --count 10 \
  --ch Z \
  --endpoint http://127.0.0.1:8546
```

- Account: Alice
- Blob size: 16 MiB
- Transactions: 10
- Blob content: repeated Z
- RPC endpoint: local node

### Small / default example

```bash
./target/release/da-spammer --account bob
```

- Account: Bob
- Blob size: 32 MiB (default)
- Transactions: 50 (default)
- Blob content: repeated b (first char of bob)
- RPC endpoint: http://127.0.0.1:8546
