---
aliases:
	- RefCell
---

parent: [[+ rust]]

```rust
use std::rc::Rc;
use std::cel::RefCell;

let x = 42;
let r1 = Rc::new(RefCell::new(x));

// create a new temporary reference, and mutate
{
  let r2 = Rc::clone(&r1);

  *r2.borrow_mut() = 43;
}

assert_eq!(*r2.borrow(), 43);
```

- allows for implementing the _interior mutability pattern_ which is a
  mechanism for working around Rust's mutability rules by allowing for
  mutation of values that have multiple references
	- Interior mutability is great for writing safe applications. Not so much safe libraries - source: https://rust-unofficial.github.io/too-many-lists/fourth-iteration.html#iter
- mutations are evaluated at runtime - if Rust's mutability laws are violated,
  the `RefCell` will panic and crash the application
- `RefCell::borrow` is the runtime equivalent to `&`
- `RefCell::borrow_mut` is the runtime equivalent to `&mut`

## Relations

- [[std..rc..Rc]] - multiple references are by default immutable in Rust. By
  wrapping the contents of `Rc` inside `RefCell` we can mutate those values
  via runtime checks
