parent: [[+ rust]]

```rust
let xs = [1,2,3];
let ys = Vec::from(xs);	// Vec<i32>

assert_eq!(xs, ys[..]);
```
