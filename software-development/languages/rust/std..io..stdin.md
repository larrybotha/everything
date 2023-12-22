Parent: [[+ rust]]

```rust
use std::io::stdin;

fn main() -> Result<(), std::io::Error> {
    let mut handle = stdin();
    let mut buffer = String::new();

    handle.read_line(&mut buffer); // wait for input from stdin

    Ok(())
}
```

## related

- [[std..io..stdout]]
