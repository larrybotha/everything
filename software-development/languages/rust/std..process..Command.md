parent: [[+ rust]]

```rust
use std::process::Command;

fn main() {
    let mut list_dir = Command::new("ls");

    println!("{:?}", list_dir.status()); // current directory's contents

    list_dir.change_directory(".."); // move to parent directory

    println!("{:?}", list_dir.status());
}
```

- a process-builder for defining how processes should be spawned

## links and resources

- https://doc.rust-lang.org/1.74.1/std/process/struct.Command.html
