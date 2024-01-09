parent: [[+ rust]]

- `async`
  - the keyword in Rust that makes specific items asynchronous
  - items that can be made async are:
    - fn
    - closures
    - blocks
  - blocks that are marked `async` are turned into [[Future]]s. A `Future` will
    not be run until is `.await`ed
- `await`
  - `.await`ing a `Future` will suspend, or block, the current function's
    execution until the future has been run to completion

## links and resources

- https://doc.rust-lang.org/1.74.1/std/keyword.async.html
- https://doc.rust-lang.org/1.74.1/std/keyword.await.html
- [Asynchronous Progammining in Rust](https://rust-lang.github.io/async-book/)
