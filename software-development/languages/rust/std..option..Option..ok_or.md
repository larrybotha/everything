parent: [[+ rust]]

```rust
fn main() {
    let xs = vec![0, 1, 2];

    let result = xs.iter().next().filter(|&x| x > &0).ok_or("ermagerd!");

    assert_eq!(result, Err("ermagerd!"));
}
```

- converts `Option<T>` to a `Result<T, E>`

## links and resources

- https://doc.rust-lang.org/1.74.0/std/option/enum.Option.html#method.ok_or
