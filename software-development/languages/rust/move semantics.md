parent: [[+ rust]]

Types that do not implement [[std..marker..Copy]], and are thus moved when not addressed by reference in statements

e.g. such as after assignment to a new variable

```rust
// Vec is not Copy
let xs = vec![1,2,3]; 
let ys = xs; // xs is moved here
// xs has been dropped, therefore not accessible
```

Variables have *move semantics* by default, unless their type is [[std..marker..Copy|Copy]]

In contrast to [[copy semantics]].