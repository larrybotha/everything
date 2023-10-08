parent: [[+ rust]]

- types that implement `Send` are safe to transfer between threads
- `Send` is automatically inferred by the compiler
- [[std..rc..Rc]] is an example of a non-`Send` type - changing an `Rc` in one
  thread, would not have its changes reflected in another thread. `Arc` is the
  thread-safe version of `Rc`
