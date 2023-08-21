parent: [[+ rust]]

```rust
let x = Some(42);

assert_eq!(x.unwrap(), 42);

let failing_case = None;

// using .unwrap is discouraged in Rust, because the following will panic!
assert_eq!(failing_case.unwrap(), 0);
```

- consumes the option, returning the contained value
- discouraged for use since it will `panic!` if the `Option` is `None`

  Instead, prefer using one of the following:

  - pattern match on the `Option`
  - use `.unwrap_or` / `.unwrap_or_else`
