parent: [[+ rust]]

```rust
pub struct SomeStruct;

impl SomeStruct {
    /// Do a panic
    ///
    /// [a description of parameter]
    ///
    /// # Panics
    ///
    /// This method will always panic
    pub fn do_a_panic(&self) {
        assert!(true == false);
    }
}
```

- allows for one to document code
- Rust will generate documentation from these doc comments. This documentation
  can be viewed using:

  ```shell
  $ cargo doc --open
  ```
