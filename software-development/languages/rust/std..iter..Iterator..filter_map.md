Parent: [[+ rust]]

```rust
fn main() {
    let xs = vec![Ok(1), Ok(2), Err("oh noes"), Ok(3)];

    xs.iter()
        .filter_map(|x| x.ok())
        .for_each(|x| println!("{}", x));

    // prints:
    // 1
    // 2
    // 3
}
```

- maps over an iterable with a condition:
    * filters values only where the closure returns `Some(value)`
    * yields only `value`
    * e.g. `Iterator<Result<T, E>>::filter_map(Result::ok)` => `Iterator<T>`
- see [[std..iter..Iterator..map_while]] for how `map_while` short-circuits the
    iterator

## related

- [[std..iter..Iterator..map_while]]

## links and resources

- https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.filter_map
