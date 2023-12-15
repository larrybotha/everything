Parent: [[+ rust]]

```rust
fn main() {
    let xs = vec![Ok(1), Ok(2), Err("oh noes"), Ok(3)];

    xs.iter()
        .map_while(|x| x.ok())
        .for_each(|x| println!("{}", x));

    // prints:
    // 1
    // 2
}
```

- maps over an iterable with a condition:
    * short-circuits on the first closure that returns `None`
    * filters values only where the closure returns `Some(value)`
    * yields only `value`
- see [[std..iter..Iterator..filter_map]] for how `filter_map` filters values
    instead of short-circuiting

## related

- [[std..iter..Iterator..filter_map]]

## links and resources

- https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.map_while
