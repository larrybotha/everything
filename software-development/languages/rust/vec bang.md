---
aliases:
	- vec!
---
parent: [[+ rust]]

```rust
let xs: Vec<i32> = vec![1, 2, 3];

// shorrhand for
let xs: Vec<i32> = Vec::from([1, 2, 3]);
```

- a [[macros|macro]] for creating a vector without using an associated method on `Vec`