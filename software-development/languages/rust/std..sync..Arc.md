parent: [[+ rust]]

```rust
// https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=9210b2e9ef382a8b6e451a6ad8bbf3be
use std::ops::Add;
use std::sync::Arc;
use std::thread;

fn main() {
    let answer = Arc::new(42);
    let mut handles: Vec<thread::JoinHandle<_>> = vec![];

    for x in (1..=5).into_iter() {
        let cloned_answer = Arc::clone(&answer);
        let handle = thread::spawn(move || {
            println!(
                "the answer to {} + {} is {}",
                x,
                cloned_answer,
                cloned_answer.add(x)
            );
        });

        handles.push(handle);
    }

    handles
        .into_iter()
        .map(|handle| handle.join())
        .for_each(|result| result.unwrap())
}
```

- a thread-safe reference counter when shared access to a value across threads
  is required
- the analogue of the non-thread-safe [[std..rc..Rc]]
- used in tandem with [[std..sync..Mutex]] when mutation of the value is
  required

## Links and resources

- https://doc.rust-lang.org/std/sync/struct.Arc.html
