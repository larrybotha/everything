parent: [[+ rust]]

Types that implement [[std..marker..Copy]], and are thus copied instead of moved when not addressed by reference in statements

e.g. such as after assignment to a new variable

```rust
// i32 is Copy
let x = 42_i32; 
let y = x; // xs is copied here
// x has not been dropped
```

In contrast to [[move semantics in Rust]].