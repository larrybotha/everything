Parent: [[+ rust]]

```rust
use std::io::{stdout, Error, Write};

fn main() -> Result<(), Error> {
    let mut handle = stdout();

    handle.write_all(b"hello world")
}
```

- construct's a new handle to `stdout` of the current process

## related

- [[std..io..stdin]]
