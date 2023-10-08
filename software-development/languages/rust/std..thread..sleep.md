parent: [[+ rust]]

```rust
use std::{thread, time::Duration};

fn main() {
    println!("sleeping for 5 seconds...");
    thread::sleep(Duration::from_secs(5));
    println!("awake!");
}
```

- blocks synchronous processing in the same way as `time.sleep` in Python
