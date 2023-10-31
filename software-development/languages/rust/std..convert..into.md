parent: [[+ rust]]

```rust
let string_from_char: String = 'x'.into();
let string_from_slice: String = "foo".into();
let char_codes: Vec<u8> = "foo".into();
let x: u8 = 0.into();
let xs: Vec<_> = [0; 100].into();		// Vec<i32>
```

- `std::convert::into` coerces values into the annotated type
- should never be implemented - we get `.into` for free on types where
  `std::convert::From` is implemented
