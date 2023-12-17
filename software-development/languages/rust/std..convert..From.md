parent: [[+ rust]]

```rust
let x = "foo".to_string();
let y = String::from("foo"); // String implements From

assert_eq!(x,y);
```

- the `From` trait is used for value-to-value conversions
- these conversions are considered _perfect_ - using `::from` or `::into` is
    guaranteed to produce a safe value

    For conversions that _may_ fail, see [[std..convert..TryFrom]]
- when implementing `From` the implementation should _never_ fail - an
    implementation of `From` is a guarantee that the conversion is safe
- the input value is consumed when using `::from`
- `From` is the inverse of `Into`, and should be preferred, as implementing
  `From` automatically provides an implementation of `Into`
- `Into` is useful when specifying trait bounds, and should be preferred over
  using `From`
  - implementing `Into` does not automatically provide the implementation of
    `From`, while the converse _is_ true
  - therefore, if one specifies `Into` as a trait bound, we guarantee support
    for types that implement either `From` or `Into`

## related

- [[std..convert..TryFrom]]

## links and resources

- https://doc.rust-lang.org/std/convert/trait.From.html
