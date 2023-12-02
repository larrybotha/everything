Parent: [[+ rust]]

```rust
use std::ops::Deref;

struct CustomBox<T>(T);

impl<T> CustomBox<T> {
    fn new(value: T) -> Self {
        Self(value)
    }
}

impl<T> Deref for CustomBox<T> {
    type Target = T;

    fn deref(&self) -> &Self::Target {
        &self.0
    }
}

fn main() {
    let x = String::from("foo");
    let boxed_x = CustomBox::new("foo".to_owned());

    // these are all equivalent dereferences
    assert_eq!(x, *boxed_x);
    assert_eq!(x, *(boxed_x.deref()));
    assert_eq!(x, *Deref::deref(&boxed_x));
}
```

- a trait that allows for _deref coercion_ on types (usually smart pointers),
  such as [[std..rc..Rc]], [[std..sync..Arc]], [[std..boxed..Box]], and
  [[std..borrow..Cow]], returning a reference to the value inside the type

  ```rust
  pub trait Deref {
      type Target: ?Sized;
      //    [1]     [2]

      // Required method
      fn deref(&self) -> &Self::Target;
      //                [3]
  }

  // 1 - the associated type of Deref is called Target
  // 2 - Target may or may not be Sized
  // 3 - deref _must_ return a reference to the value inside the type - if it
  //    didn't return a reference, the value would be moved, and the type would
  //    no longer have access to that value
  ```

- allows for customising the behaviour of `*`
- the values inside smart pointers that implement `Deref` can be interacted
  with as if they were normal references
- it should _only_ be implemented for smart pointers - see Rust docs

## links and resources

- https://doc.rust-lang.org/std/ops/trait.Deref.html
- https://doc.rust-lang.org/1.74.0/book/ch15-02-deref.html
- https://doc.rust-lang.org/1.74.0/reference/expressions/operator-expr.html#the-dereference-operator
- https://doc.rust-lang.org/1.74.0/reference/expressions/method-call-expr.html
- https://doc.rust-lang.org/1.74.0/reference/type-coercions.html
