Parent: [[+ rust]]

```rust
use std::io::{self, Write};

fn stdout_implicit_sync() -> Result<(), io::Error> {
    io::stdout().write_all(b"hello world\n")
}

fn stdout_explicit_sync() -> Result<(), io::Error> {
    let stdout = io::stdout();
    let mut handle = stdout.lock();

    handle.write_all(b"hello world\n")
}

fn main() -> Result<(), io::Error> {
    stdout_implicit_sync()?;

    stdout_explicit_sync()?;

    Ok(())
}
```

- construct's a new handle to `stdout` of the current process
- each handle is a reference to a shared global buffer - access is synchronised
    implicitly via a mutex, but can be managed explicitly via `Stdout::lock`
- writing frequently to `stdout` can be expensive - use [[std..io..BufWriter]]
    to buffer many writes

## related

- [[std..io..stdin]]
- [[std..io..stderr]]
- [[std..io..BufWriter]]

## links and resources

- https://doc.rust-lang.org/1.74.1/std/io/fn.stdout.html
