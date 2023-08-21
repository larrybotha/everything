parent: [[+ rust]]

```rust
use std::cell::RefCell;

let cell = RefCell::new(42);
let x = cell.into_inner(); // consumes cell, dropping it

assert_eq!(x, 42;)
```

- extracts a value out of a cell
- consumes the cell
