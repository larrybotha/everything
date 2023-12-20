parent: [[+ rust]]

```rust
// without .as_ref, x is consumed:
let x = Some(String("foo"));
let y = x.map(|v| v + "bar"); // x is consumed by .map

assert_eq!(y, Some("foobar"));

// with .as_ref, x is not consumed:
let x = Some(String("foo"));
let y = x.as_ref().map(|v| v.to_owned() + "bar");

assert_eq(x, Some("foo"));
assert_eq(y, Some("foobar"));
```

- converts `Option<T>` to `Option<&T>`
- `Option::map` consumes the option
- if we want to perform an operation with the value inside the option, and
  without consuming it, we can get a reference to the value instead by using
  `Option::as_ref`

## related

- [[std..borrow..Borrow]]
- [[std..convert..AsRef]]
