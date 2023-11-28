Parent: [[+ rust]]

```rust
use std::borrow::Cow;

fn main() {}
```

- an enum allowing for lazy cloning of data when mutation or ownership is required
  - the value a `Cow` contains is either:
    - `Cow::Borrowed`, or
    - `Cow::Owned`
- Rust's implementation of [[copy-on-write]], although it's more accurately
  described as _clone_-on-write since `Clone` allows for additional logic,
  such as recursive cloning of nested data, whereas `Copy` is a simpler
  process
- can be thought of as _ownership on demand_
- `Cow` is a smart pointer that is useful for sharing data that mostly doesn't
  need to be mutated, but sometimes does
  - e.g. when expecting valid utf8 data that on the odd occasion requires a transformation
- `Cow` implements [[std..ops..Deref]] - properties and non-mutable methods
  on the contained value can be accessed directly via the `Cow`
- from [The Secret Life of Cows](https://deterministic.space/secret-life-of-cows.html)
  - to write fast applications, one must know:
    - exactly where your data lives,
    - that it is efficiently stored,
    - that it is removed as soon as you stop using it,
    - and that you don’t copy it around needlessly.
  - allocating memory is expensive - `Cow` allows for mitigating allocations

## related

- [[std..rc..Rc]]

## links and resources

- https://www.reddit.com/r/rust/comments/v1z6bx/what_is_a_cow/
- https://deterministic.space/secret-life-of-cows.html
- https://doc.rust-lang.org/std/borrow/enum.Cow.html
- https://dhghomon.github.io/easy_rust/Chapter_42.html
- https://dev.to/kgrech/6-things-you-can-do-with-the-cow-in-rust-4l55
