parent: [[+ rust]]

```rust
type Metres = i32;

let x: Metres = 5;

assert_eq!(x + 5, 10);
```

- useful for naming complex types
- are interpreted as the types they alias - not as distinct types
- unlike [[newtypes]], do not benefit from type checking
- type aliases can be generic:

  ```rust
  type GenericResult<T> = Result<T, std::io::Error>;

  let string_result: GenericResult<String> = Ok("foo");
  let unit_result: GenericResult<()> = Ok(());
  ```
