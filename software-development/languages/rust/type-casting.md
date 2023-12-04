parent: [[+ rust]]

```rust
fn average(xs: &[f64]) -> f64 {
    let sum: f64 = xs.iter().sum();
    // xs.len() returns a usize, and we can't divide f64 by usize, so we
    // cast it to f64 using the binary 'as' operator
    let len: f64 = xs.len() as f64;

    sum / len
}

fn main() {
    let xs = vec![1.1, 2.2, 3.3, 4.4];

    assert_eq!(average(&xs[..]), 2.75);
}
```

## links and resources

- https://doc.rust-lang.org/1.74.0/reference/expressions/operator-expr.html#type-cast-expressions
