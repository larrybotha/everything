parent: [[+ rust]]

```rust
use std::rc::Rc;

let a = 42;
// 1 reference
let x = Rc::new(a);

{
  let y = Rc::clone(&x);
  // 2 references
  let result = Rc::try_unwrap(y);

  assert_eq!(result, Err(42));
} // 1 reference

let result = Rc::try_unwrap(x);

assert_eq!(result, Ok(42);
```

- `Rc::try_unwrap` will return a `Result` of the wrapped value:
  - if there is only 1 reference, the result will be `Ok(x)`,
  - else the result will be `Err(x)`
- this is useful in situations where you want to take ownership of or drop
  the contained value
- `std::sync::Arc` implements the same method with the same semantics
