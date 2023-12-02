---
aliases:
  - ToOwned
---

parent: [[+ rust]]

```rust
pub trait ToOwned {
    type Owned: Borrow<Self>;
    //    [1]

    // Required method
    fn to_owned(&self) -> Self::Owned;
    //                       [2]

    // Provided method
    fn clone_into(&self, target: &mut Self::Owned) { ... }
}


// 1 - the associated type of ToOwned, Owned, _must_ implement Borrow,
//      which means that it must be possible to create references to
//      the type
// 2 - calling .to_owned() on the value must return an owned value of
//      the type
```

- types that implement `Clone` can be converted from a borrowed value to an
  owned value, i.e. `&T` to `T`

  This doesn't generalise to all borrowed types, e.g. smart pointers.
  `ToOwned` generalises `Clone` to any borrowed type that implements it

- the associated type of the `ToOwned` trait must implement
  [[std..borrow..Borrow]]

## links and resources

- https://doc.rust-lang.org/std/borrow/trait.ToOwned.html
