parent: [[+ rust]]

A naive example:

```rust
use std::mem;

let mut x = 4;
let y = mem::replace(&x, 5);

assert_eq!(y, 4);
assert_eq!(x, 5);
```

A more informative example:

```rust
struct Foo {
    value: i32,
}

impl Foo {
    fn update_value(&mut self, x: i32) -> i32 {
        // set and return the value without moving self.value
        let old_value = mem::replace(&mut self.value, x);

        old_value
    }

    // will break compilation
    fn invalid_update_value(&mut self, x: i32) -> i32 {
        // This is an error -
        // attempting to move ownership of self.value, when we
        // have a reference
        let old_value = self.value;
        self.value = x;

        old_value
    }
}
```

- `std::mem::replace` allows for replacing a value in memory
  in-place without affecting ownership
- this is useful in scenarios where you have a reference to a
  value, but you want take ownership of the new value while
  replacing it with another value
