parent: [[+ rust]]

```rust
// functions with generics implicitly
// require types with known sizes
// i.e.
fn generic<T>(x: T) {
    // ...
}

// is actually the following
fn generic<T: Sized>(x: T) {
    // ...
}
```

- types with a constant size known at compile time
- if the compiler is complaining about `Sized` types, you likely need to wrap
  the value in a smart pointer
- the `Sized` trait is automatically implemented for every type where the size
  of the type is known
- [[dynamically sized types]] are also known as DSTs or unsized types
- all values of a given type in Rust must use the same amount of memory

  - e.g. we always know that `i32` will occupy 32 bytes, but with `str`
    (NOTE: no `&`) we don't know that:

    ```rust
    // str can't represent values of differing sizes
    let x: str = "foobar"; // 6 bytes
    let y: str = "quux";   // 4 bytes
    ```

    `str` doesn't have the luxury that numbers do - strings can be any length,
    i.e. they are dynamically sized types

    `&str`, however, is composed of 2 values that we know the size of:

    - the starting point in memory i.e. pointer, a `usize`
    - the length of the string, a `usize` again

    This is the same as using `Box` or `Rc` to hold references to values whose
    sizes we don't know, such as in recursive structures

- the values of dynamically sized types must always be behind some kind of
  pointer
- functions with generics implicitly require those generic arguments to have
  known sizes. This can be opted out of by using `<T: ?Sized>` as a bound, which
  translates to "T may or may not be `Sized`". This syntax is unique to `Sized`
- [variables](https://doc.rust-lang.org/reference/variables.html), function parameters, [const](https://doc.rust-lang.org/reference/items/constant-items.html) items, and [static](https://doc.rust-lang.org/reference/items/static-items.html) items must be `Sized`, as stated in https://doc.rust-lang.org/reference/dynamically-sized-types.html

## links and resources

- https://doc.rust-lang.org/std/marker/trait.Sized.html