parent: [[+ rust]]

```rust
let string_slice = "foo";						// &str
let string1 = String::from("bar");	// String
let string2 = "bar".to_string();		// String

assert_eq!("foo", string_slice.to_string().as_str());
assert_eq!(String::from("bar"), string1.as_str().to_string());
```

- `&str` is allocated on the heap, and is constant for the duration of the
  application's lifetime
  - slices are references to arrays. `&str` is actually `&[u8]` - a slice of an
    array of `u8` values
- `String::as_str` and `&str::to_string` are isomorphic operations
