parent: [[+ rust]]

```rust
fn factorial(n: u64) -> u64 {
    (1..=n).into_iter().fold(1, |acc, x| acc * x)
}
```

- `fold` operates the same as `reduce` does in Javascript:
  - it accepts an initial value
  - it accepts a closure which:
    - accepts the accumulator
    - accepts the next value in the iterator
    - returns the transformed value

## links and resources

- https://doc.rust-lang.org/1.73.0/std/iter/trait.Iterator.html#method.fold
