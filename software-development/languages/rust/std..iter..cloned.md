parent: [[+ rust]]

```rust
let xs = vec![String::from("foo"), String::from("bar")];
let ref_xs: Vec<_> = xs.iter().collect();
let cloned_xs: Vec<_> = xs.iter().cloned().collect();

assert_eq!(&xs[0], ref_xs[0]);
assert_eq!(xs[0], cloned_xs[0]);

// for integers, .cloned is the same as destructuring the reference
// while mapping
let xs = vec![1,2,3];
let xs_cloned: Vec<_> = xs.iter().cloned().collect();
let xs_mapped: Vec<i32> = xs.iter().map(|&x| x).collect();

assert_eq!(xs_cloned, xs_mapped);
```

- converts from `Iterator<&T>` to `Iterator<T>`
- for performance reasons, cloning should be done as late as possible,
  e.g. prefer `transform -> clone -> collect` over `clone -> transform -> collect`

## related

- [[std..iter..Iterator..collect]]

## links and resources

- https://doc.rust-lang.org/1.73.0/std/iter/trait.Iterator.html#method.cloned
