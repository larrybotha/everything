parent: [[+ rust]]

```rust
use std::mem;

let mut x = Some(41);
// mem::replace will:
//  - set the mutable value to the second argument
//  - return the value of the first argument
let y = mem::replace(&mut x, None);

assert_eq!(y, Some(41));
assert_eq!(x, None);

// The above is encapsulated by using Option::take, i.e. .take will:
//  - set the mutable option to None-
//  - return the value of the option
let mut x = Some(41);
let y = x.take();

assert_eq!(y, Some(41));
assert_eq!(x, None);
```

- `Option::take` is shorthand for what `std::mem::replace` does when replacing
  a value in memory with `None`
  - sets the variable or field to None
  - returns the value that the variable or field originally contained
- see [[std..mem..replace]]
