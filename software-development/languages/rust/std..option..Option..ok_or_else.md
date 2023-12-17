
Parent: [[+ rust]]

```rust
fn main() {
    let xs = vec![0, 1, 2];

    let result = xs.iter()
      .next()
      .filter(|&x| x > &0)
      .ok_or_else(|| {"ermagerd!"});

    assert_eq!(result, Err("ermagerd!"));
}
```

- lazily transforms `Option<T>` to `Result<T, E>`
- prefer using this method over [[std..option..Option..ok_or]]
## related

- [[std..option..Option..ok_or]]
- [[std..result..Result..ok]]
## links and resources

https://medium.com/@techhara/rust-tip-and-trick-2-5a92641191f6