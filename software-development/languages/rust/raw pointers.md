parent: [[+ rust]]

```rust
// represented as
*const T
// or
*mut T
```

- raw pointers are a feature of unsafe Rust
  - have no inherent aliasing rules - i.e. Rust's borrowing rules do not apply.
    See the [Aliasing docs](https://doc.rust-lang.org/rust-by-example/scope/borrow/alias.html)
    Rust By Example
  - have no lifetimes
  - can be null
  - can be misaligned
  - can be dangling
  - can point to uninitialised memory
  - can be cast to point to a different type
  - can be cast to be mutable
- they are similar to pointers in C
