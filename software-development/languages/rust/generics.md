parent: [[+ rust]]

```rust
struct GenericType<T> {
    value: T,
}

// generic types must be defined with impl<T>
impl<T> GenericType<T> {
    fn new(value: T) -> Self {
        GenericType { value }
    }
}

fn generic_function<T>(x: T) {
    // ...
}
```

- generics are a way of generalising types and functions
- functions that accept generics implicitly require that the types are `Sized` -
  see the code example in [[Sized]]
- generic types with implementations must specify their types in the `impl`
  definition using `impl<T>`

## Links and resources

- [Generic Data Types](https://doc.rust-lang.org/stable/book/ch10-01-syntax.html)
- [Bounds](https://doc.rust-lang.org/rust-by-example/generics/bounds.html)
