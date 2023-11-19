parent: [[+ rust]]

```rust
use std::collections::HashMap;

fn main() {
    let xs: Vec<_> = vec![HashMap::from([('a', 1)]), HashMap::from([('b', 2)])];
    let sum_flat_map = xs.iter().flat_map(|x| x.values()).sum::<i32>();
    let sum_flatten = xs.iter().map(|x| x.values()).flatten().sum::<i32>();

    assert_eq!(sum_flat_map, sum_flatten);
}
```

- like `Array.prototype.flatMap` in Javascript, maps over a value, flattens
  `Iterator<Iterator<T>>` to `Iterator<T>`
- syntactic sugar for `.map(transformFn).flatten()`

## related

- [[std..option..Option..flatten]]
- [[std..option..Option..and_then]]
