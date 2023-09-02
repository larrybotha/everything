parent: [[+ rust]]

```rust
use std::iter::{DoubleEndedIterator, Iterator};

struct MyStruct {
    // ...
}

impl Iterator for MyStruct {
    type Item = i32;

    pub fn next(&mut self) -> Option<i32> {
        // ...
    }
}

impl DoubleEndedIterator for MyStruct {
    pub fn next_back(&mut self) -> Option<i32> {
        // ...
    }
}

fn main() {
    let xs = MyStruct {};

    for x in xs.iter().rev() {
        // ...
    }
}
```

- allows for iterating in reverse on a type
- requires that the type have a finite number of elements, i.e. not an
  open-ended range
