parent: [[+ rust]]

```rust
let result: Result<i32, &str> = Ok(42);

assert_eq!(result.ok(), Some(42));
```

- `Result::ok` converts from `Result<T, E>` to `Option<T>`