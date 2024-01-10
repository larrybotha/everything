parent: [[+ rust]]

```rust
fn fib(n: i32) -> i32 {
    todo!()
}
```

- indicates unfinished code
- useful during prototyping if one wants type analysis to pass
- using `cargo expand`, expands to:

  ```rust
  ::core::panicking::panic("not yet implemented")
  ```
