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

e.g. using `cargo expand` on a binary that uses `tokio::main` to determine what
the macro is generating:

```rust
// ...

use my_binary::run;

fn main() -> Result<(), std::io::Error> {
    // contain the original body of `main` in a block, and create a future from
    // it
    let body = async { run().await };

    #[allow(clippy::expect_used, clippy::diverging_sub_expression)]
    {
        return tokio::runtime::Builder::new_multi_thread()
            .enable_all()
            .build()
            .expect("Failed building the Runtime")
            // block until the future has been completed
            .block_on(body);
    }
}
```

`main` cannot be `async`, because who will poll it - it's a top-level call.
`tokio::main` gives the illusion that `main` is async, but in reality it is
taking our original body, creating a future from it, and using its own runtime
to poll the future

## links and resources

- https://doc.rust-lang.org/1.74.1/std/keyword.async.html
- https://doc.rust-lang.org/1.74.1/std/keyword.await.html
- [Asynchronous Progammining in Rust](https://rust-lang.github.io/async-book/)
