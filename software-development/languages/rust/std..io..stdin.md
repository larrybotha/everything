Parent: [[+ rust]]

```rust
use std::io::stdin;

use std::io::{self, Write};

fn stdin_implicit_sync() -> Result<(), io::Error> {
    io::stdin().write_all(b"hello world\n")
}

fn stdin_explicit_sync() -> Result<(), io::Error> {
    let stdin = io::stdin();
    let mut handle = stdin.lock();

    handle.write_all(b"hello world\n")
}

fn main() -> Result<(), io::Error> {
    stdin_implicit_sync()?;

    stdin_explicit_sync()?;

    Ok(())
}
```

## related

- [[std..io..stdout]]

## links and resources

- https://doc.rust-lang.org/1.74.1/std/io/fn.stdin.html
