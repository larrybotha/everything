Parent: [[+ rust]]

```rust
// https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=9210b2e9ef382a8b6e451a6ad8bbf3be
use std::borrow::Cow;

fn replacer<'a>(x: &'a str, search: &str, replacement: &str) -> Cow<'a, str> {
    match x.contains(search) {
        true => x.replace(search, replacement).into(),
        false => x.into(),
    }
}

fn print_cow(x: Cow<'_, str>) {
    match x {
        Cow::Borrowed(v) => println!("value is borrowed: {}", v),
        Cow::Owned(v) => println!("value is owned: {}", v),
    }
}

fn main() {
    let search = "x";
    let replacement = "o";
    let cow_a = replacer("fxx", search, replacement);
    let cow_b = replacer("foo", search, replacement);

    assert_eq!(cow_a, String::from("foo"));
    assert_eq!(cow_b, "foo");

    print_cow(cow_a);
    print_cow(cow_b);
}
```

- the _clone on write_ enum in Rust, allowing for lazy cloning of data:

  ```rust
  pub enum Cow<'a, B>
  //           [1]
  where
      B: 'a + ToOwned + ?Sized,
      // [2]    [3]       [4]
  {
      Borrowed(&'a B),
      // [5]
      Owned(<B as ToOwned>::Owned),
      // [6] [     7    ]    [8]
  }

  // 1 - Cow has a lifetime parameter - the value it accepts must be a
  //    reference
  // 2 - the type B is that reference
  // 3 - B must implement ToOwned
  // 4 - by default, all generics are Sized in Rust. We know this value is a
  //    reference, and a reference _is_ sized, so we tell Rust that the value
  //    itself doesn't need to be Sized
  // 5 - the Borrowed variant of Cow will contain a reference to the type B,
  //    with the given lifetime
  // 6 - the Owned variant is the result of calling B.into(), which will
  //    convert the value from a reference to an owned value
  // 7 - interpret B in terms of its implementation of ToOwned...
  // 8 - this 'Owned' represents the associated type of ToOwned. Cow::Owned
  //    contains a value that is the ToOwned::Owned type that B.to_owned()
  //    resolves to
  ```

Creating a new `Cow` can be done with either a reference or an owned type - the
resulting value depends on:

- whether the input is a reference or not
  e.g. `[T]` is not allowed as an argument to `Cow::from` because `[T]` does
  not implement `std::borrow::Borrow`, but `&[T]` _does_. `Cow::from([&[T]])`
  yields `Cow::Borrowed(&[T])`

  Alternatively, `Vec<T>` _does_ implement `std::borrow::Borrow`, so

- whether the input required cloning or not

e.g.

```rust
use std::borrow::Cow;

fn main() {
    let xs = vec![1, 2, 3];
    let x = Cow::from(&xs);

    // x is a Cow::Borrowed - notice that Borrowed contains a reference
    assert_eq!(x, Cow::Borrowed(&vec![1, 2, 3]));

    let x = Cow::from(xs);

    // x is Cow::<[i32]>::Owned, xs has been moved into the Cow
    assert_eq!(x, Cow::<[i32]>::Owned(vec![1, 2, 3]));

    let ys = [1, 2, 3];
    let y = Cow::from(&ys[..]);

    // y is Cow::Borrowed
    assert_eq!(y, Cow::Borrowed(&[1, 2, 3]));
}
```

- `Cow` is similar to the [[copy-on-write]] concept, although that behaviour is
  provided by [[std..rc..Rc]] and [[std..sync..Arc]]. `Clone` allows for
  additional logic, such as recursive cloning of nested data, whereas `Copy`
  is a simpler process
- the `Cow::Borrowed` type will usually be a reference to a type that is
  allocated on the stack... the reference is cheap, and _only if_ something
  needs to be done with it, such as mutation, do we then clone it
  - for this to happen, the type has to implement [[std..borrow..ToOwned|ToOwned]].
    Why? Because in order for `Cow` to convert a value from `Cow::Borrowed` to
    `Cow::Owned`, the value must be able to be converted from a reference to a
    concrete type. In the case of `&str`, we have `&str::ToOwned -> String`.
    With arrays we have `&[T]::ToOwned -> Vec<T>`
- can be thought of as _optional ownership_
- `Cow` is a smart pointer that is useful for sharing data that mostly doesn't
  need to be mutated, but sometimes does
  - e.g. when expecting valid utf8 data that on the odd occasion requires a transformation
- `Cow` implements [[std..ops..Deref]] - properties and non-mutable methods
  on the contained value can be accessed directly via the `Cow`
- from [The Secret Life of Cows](https://deterministic.space/secret-life-of-cows.html)
  - to write fast applications, one must know:
    - exactly where your data lives
    - that it is efficiently stored
    - that it is removed as soon as you stop using it
    - and that you don’t copy it around needlessly
  - allocating memory is expensive - `Cow` allows for mitigating allocations by
    only allocating when it is explicitly required, e.g. when working with a
    reference, and something about that reference needs to be modified
    - this also makes for a good practice when working with iterable values,
      such as strings and arrays - slices are references to sections of
      strings and arrays - if we need to work with a subsection of an array or
      string, it's better to work with a slice of that value, which is a
      reference, than it is to allocate new memory with a new value

## related

- [[std..rc..Rc]]
- [[slice]]

## links and resources

- https://www.reddit.com/r/rust/comments/v1z6bx/what_is_a_cow/
- https://deterministic.space/secret-life-of-cows.html
- https://doc.rust-lang.org/std/borrow/enum.Cow.html
- https://dhghomon.github.io/easy_rust/Chapter_42.html
- https://dev.to/kgrech/6-things-you-can-do-with-the-cow-in-rust-4l55
