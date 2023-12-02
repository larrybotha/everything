---
aliases:
  - std::borrow::Borrow
---

parent: [[+ rust]]

```rust
use std::borrow::Borrow;

let x = String::from("foo");

assert_eq!(x.borrow() as &String, &x);
```

- a trait that allows types to express that they can be borrowed
- types are _borrowed as_ some type `T` when the type implements `Borrow<T>`,
  e.g. `String` and `&str`, `Box<T>` as `T`

## links and resources

- https://doc.rust-lang.org/std/borrow/trait.Borrow.html
