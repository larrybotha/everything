parent: [[+ rust]]

```rust
use std::cmp::{Ord, Ordering};

fn main() {
    let x = 5;
    let y = 6;

    assert_eq!(x.cmp(&y), Ordering::Less);
    assert_eq!(Ord.cmp(&y, &x), Ordering::Greater);
}
```

- `Ord` is implemented by values that can be compared
- `Ordering` is the enum that can be used to determine the outcome of comparing
  values
