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
    let mut xs = MyStruct {};

    for x in xs.iter().rev() {
        // ...
    }
}
```

- allows for iterating in reverse on a type
- requires that the type have a finite number of elements, e.g. not an
  open-ended range
- structures that implement `DoubleEndedIterator` are [[deque|deques]]