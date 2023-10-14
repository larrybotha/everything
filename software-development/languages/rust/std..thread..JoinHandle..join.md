parent: [[+ rust]]

```rust
use std::thread;

// create a thread builder that allows us spawn threads
let thread_builder = thread::Builder::new();
let join_handle: thread::JoinHandle<_> = thread_builder.spawn(|| {
	// do some work asynchronously...
}).unwrap();

// join the thread, blocking any further processing until the thread is
// done with its work
join_handle.join().expect("Unable to join thread");
```

- `std::thread::JoinHandle::join` will block a thread synchronously until the
  thread is done doing its work
- if its associated thread is finished doing its work, it returns immediately
- if its associated thread `panic`s, it'll return an `Err`
- `.join()` will take ownership of the join_handle
