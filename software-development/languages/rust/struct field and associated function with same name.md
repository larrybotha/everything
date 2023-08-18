parent: [[+ rust]]

```rust
struct Foo {
	value: i32
}

impl Foo {
	fn value(&self) -> &i32 {
		&self.value
	}
}

let foo = Foo { value: 5 };

assert_eq!(&foo.value, foo.value())
```

- Rust allows for structs to have the same name as an associated function
- Rust knows which value to use based on the context
  - if using a basic accessor, return the field
  - if calling a function... call the function
