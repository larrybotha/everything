parent: [[+ rust]]

```rust
let x = Some(Some(41));
let y = Some(None);

assert_eq!(x.flatten(), Some(41));
assert_eq!(y.flatten(), None);
```

- `Option::flatten` flattens a single level of nesting in the option
- [[std..option..Option..and_then|Option::and_then]] is the `.flatmap`
  analogue
