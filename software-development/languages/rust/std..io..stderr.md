Parent: [[+ rust]]

```rust
use std::io::{self, Write};

fn stderr_implicit_sync() -> Result<(), io::Error> {
    io::stderr().write_all(b"hello world\n")
}

fn stderr_explicit_sync() -> Result<(), io::Error> {
    let stderr = io::stderr();
    let mut handle = stderr.lock();

    handle.write_all(b"hello world\n")
}

fn main() -> Result<(), io::Error> {
    stderr_implicit_sync()?;

    stderr_explicit_sync()?;

    Ok(())
}
```

- constructs a new handle to the current process's `stderr`
- unlike `stdout` and `stdin`, is not buffered

## related

- [[std..io..stdin]]
- [[std..io..stdout]]


## links and resources

- https://doc.rust-lang.org/1.74.1/std/io/fn.stderr.html
