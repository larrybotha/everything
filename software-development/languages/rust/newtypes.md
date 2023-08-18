parent: [[+ rust]]

```rust
struct IntVec(Vec<i32>);

impl fmt::Display for IntVec {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        write!(f, "[{}]", self.0.join(", "))
    }
}

let int_vec = IntVec([1,2,3]);
```

- useful for implementing traits on types that are not defined in the crate
- without implementing `Deref` the newtype doesn't have access to any of the methods in the wrapped type without destructuring it
- useful for differentiating between discrete values of the same type:

  ```rust
  struct Centimetres(u32);
  struct Metres(u32);

  // Implement addition within structures...

  let c = Centimetres(5);
  let m = Metres(5);

  // invalid without writing implementations addition between types
  let total = c + m;
  ```

  in contrast to how [[Type aliases]] work

- useful for hiding implementation details of types
