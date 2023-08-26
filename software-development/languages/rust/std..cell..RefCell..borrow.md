parent: [[+ rust]]

```rust
use std::cell::RefCell;

let x = String::from("foo");
let cell = RefCell::new(x);

{
	let z = cell.borrow();

	assert_eq!(*z, String::from("foo"));
}
```

- `RefCell::borrow` is akin to `&` during compile-time
- `RefCell::borrow` returns a `Ref<'b, T>` - the runtime equivalent of a borrowed
  value
- `Ref` behaves similarly to `&`
- the lifetime of the value inside `Ref` is tied to the lifetime of `Ref` -
  _not_ `RefCell`. Attempting to reference the value of a `RefCell` outside of
  its current scope will fail, because the value inside the `RefCell` after
  borrowing is tied to the `Ref`, _not_ the `RefCell`:

  ```rust
  use std::cell::RefCell;

  fn get_ref(ref: Ref)

  let x = String::from("foo");
  let cell = RefCell::new(x);
  let mut y = String::new();

  {
  	let ref_x = cell.borrow(); // Ref<'b, String>

  	// this will not compile - ref_x lives only as long as this block, so
  	// we can't // assign the reference to something outside of the scope -
  	// we'd have an invalid reference
  	y = *ref_x;
  } // ref_x has been dropped, references to its value would no longer be valid
  ```
