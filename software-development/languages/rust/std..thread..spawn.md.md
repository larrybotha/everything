---
aliases:
  - std::thread::spawn
---

parent: [[+ rust]]

```rust
use std::thread;

fn main() {
  let xs: Vec<i32> = vec![1,2,3];
  // Move xs into the closure
  // We need to guarantee that by
  // the time the thread runs that
  // xs is still a valid place 
  // in memory
  let handle = thread::spawn(move || {
    println!("xs: {:?}", xs)
  });

  peintln!("about to print xs...");

  handle.join().unwrap();
}
```

- spawns a new thread to perform work in
- returns a `std::thread::JoinHandle`
- values inside the closure must be `move`d - why...? Because we don't know how long the thread may run - we don't know if the thread will outlive the values of closes over, so to ensure that the thread doesn't attempt to access memory that is no longer pointing to what we expect, we `move` the values into the closure to ensure they live long enough for the closure to use them safely

## related

- [[std..thread..JoinHandle..join]]