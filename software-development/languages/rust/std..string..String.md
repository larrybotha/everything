parent: [[+ rust]]

```rust
let s = String::from("hello");

let x = String::from("foo");
let y = String::from("bar");
// Concatenation of strings requires
// is defined by String::add
//   - the first value must be String
//   - the second value must be &str
let xy = x + &y;
// syntactic sugar for
//let xy = x.add(&y);
```

- a growable, utf-8 encoded string
- can be converted to `&str` in a number of ways:

  1.  using a reference and a range:

      ```rust
      let my_string = String::from("Hello, world!");
      let my_str = &my_string[..];
      ```

  1.  Using the `as_str` method:

      ```rust
      let my_string = String::from("Hello, world!");
      let my_str: &str = my_string.as_str();
      ```

  1.  Using `deref` coercion:

      ```rust
      use std::ops::Deref;

      let my_string = String::from("Hello, world!");
      let my_str: &str = my_string.deref();
      ```

  1.  Using the `into_boxed_str` method:

      ```rust
      let my_string = String::from("Hello, world!");
      let my_boxed_str: Box<str> = my_string.into_boxed_str();
      let my_str: &str = &my_boxed_str;
      ```

  1.  Using the `into_bytes` method and then converting the bytes slice to `&str`:
      ```rust
      let my_string = String::from("Hello, world!");
      let my_bytes = my_string.into_bytes();
      let my_str: &str = std::str::from_utf8(&my_bytes).unwrap();
      ```
