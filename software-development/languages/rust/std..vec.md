parent: [[+ rust]]

```rust
let xs = Vec::from([1, 2, 3]);
let ys = vec![1, 2, 3]; // shorthand for Vec::from[some_array]
let zs: Vec<_> = (1..4).collect();
```

- a [[macros|macro]] for creating a vector without using an associated method on `Vec`
- a vector can be converted to a slice using [[std..vec..index]]
