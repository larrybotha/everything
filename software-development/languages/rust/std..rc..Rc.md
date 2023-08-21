parent: [[+ rust]]

```rust
use std::rc::Rc;

let x = 42;
let r1 = Rc::new(x);

assert_eq!(Rc::strong_count(&r1), 1);

{
  // increment the reference count
  let r2 = Rc::clone(&r1);

  assert_eq!(Rc::strong_count(&r2), 2);

  // unable to unwrap if reference count > 1
  let result = Rc::try_unwrap(&r2);

  assert_eq!(result, Err(42));
} // decrement the reference count

assert_eq!(Rc::strong_count(&r1), 1);

// remove the final reference, which:
//  - brings the reference count to 0
//  - indicates to Rust that 'result' must be dropped
let result = Rc::try_unwrap(&r1);

assert_eq!(result, Ok(42));

// result has been dropped - we can't access it
// assert_eq!(Rc::strong_count(&r1), 1);
```

- a pointer type that allows for reference counting of heap-allocated values
  - multiple references to the value may exist at the same time, and thus
  - the value is immutable
- the `Rc` is dropped as soon as it's reference count reaches 0
- useful when shared references to values are required
- if interior mutability is required, needs to be used in conjunction with [[std..rc..RefCell]]

## Relations

- [[std..boxed..Box]] - contrasts with Box
- [[std..rc..RefCell]] - required for mutating the contents of `Rc`
- [[std..rc..Rc..try_unwrap]] - returns a `Result` for attempting to remove the value from
  the `Rc` - is only `Ok` if `Rc::strong_count` is 1
