# Monad Dev net contract depolyment 

## 1. Fork this Repo & give star
## 2. Login with Gitpod.io

## 3. Install Dependency 

```
curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
```
```
source $HOME/.cargo/env
```
```
curl https://sh.rustup.rs -sSf | sh
```

```
curl -L https://foundry.paradigm.xyz | bash
```

```
source /home/gitpod/.bashrc
```

```
foundryup
```

## 5. Monad Template
```
forge init --template monad-developers/foundry-monad zotac
```
```
cd zotac
```

### 6. Need to change foundry.toml file with following command

```
[profile.default]
src = "src"
out = "out"
libs = ["lib"]

# Monad Configuration

eth-rpc-url = "https://rpc-devnet.monadinfra.com/rpc/3fe540e310bbb6ef0b9f16cd23073b0a"

chain_id = 20143

# Etherscan Configuration
[etherscan]

monadDevnet = { key = "DUMMY_VALUE", url = "https://explorer.monad-devnet.devnet101.com/", chain = 20143 }

```
### 7. Input 1 and proceed 

```
. "$HOME/.cargo/env"
```

### 8. With the RISC-V target:

```shell
rustup target add riscv32i-unknown-none-elf
```

### 9. Then install the Nexus zkVM:

```shell
cargo install --git https://github.com/nexus-xyz/nexus-zkvm cargo-nexus --tag 'v0.2.0'
```

### 10. Create a new Nexus project

```shell
cargo nexus new nexus-project
```

This will create a new Rust project directory with the following structure:

```shell
./nexus-project
├── Cargo.lock
├── Cargo.toml
└── src
    └── main.rs
```

### 11. Move to Directory, Replace the code and press CNTL+X, Y, Enter

```
cd nexus-project
cd src
nano main.rs
```
As an example, you can change the content of `./src/main.rs` to:

```rust
#![no_std]
#![no_main]

fn fib(n: u32) -> u32 {
    match n {
        0 => 0,
        1 => 1,
        _ => fib(n - 1) + fib(n - 2),
    }
}

#[nexus_rt::main]
fn main() {
    let n = 7;
    let result = fib(n);
    assert_eq!(result, 13);
}
```


### 12. Run your program

```bash
cargo nexus run
```

### 13. step-by-step execution trace on the NVM, run:

```bash
cargo nexus run -v
```

### 14. Prove your program - Generate a proof for your Rust program using the Nexus zkVM.

```shell
cargo nexus prove
```

### 15. Verify your proof - Finally, load and verify the proof:

```shell
cargo nexus verify
```


#### Most importanly  commit and push the repo in github 

