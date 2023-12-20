---
aliases:
  - Copy
---
parent: [[+ rust]]

A trait in Rust that gives a type [[copy semantics]].

- `Copy` indicates that a type is safe to copy when it is assigned, and that it
    doesn't need to be moved.

    See the `Arithmetic` example at
    https://blog.logrocket.com/disambiguating-rust-traits-copy-clone-dynamic/#understanding-copy-trait
- new types have [[move semantics]] by default
- a type may implement `Copy` if all of its contained types are `Copy`
- `Copy` forms part of a type's public API - restoring a type to have
  [[move semantics]] may introduce breaking changes to your API
- any type implementing [[std..ops..Drop]] cannot be `Copy`

## Links and resources

- https://doc.rust-lang.org/nightly/std/marker/trait.Copy.html
- https://blog.logrocket.com/disambiguating-rust-traits-copy-clone-dynamic/#understanding-copy-trait
