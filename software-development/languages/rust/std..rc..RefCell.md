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
- `RefCell::borrow` is the runtime equivalent to `&`
- `RefCell::borrow_mut` is the runtime equivalent to `&mut`

## Relations

- [[std..rc..Rc]] - multiple references are by default immutable - wrapping the contents of `Rc` allows for mutation of these values
