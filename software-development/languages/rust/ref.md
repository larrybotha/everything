parent: [[+ rust]]

```rust
#[derive(Debug)]
struct Foo {
	a: i32,
	b: String,
};

let x = Some(Foo { a: 42, b: String::from("bar") });

// The following is invalid! We cannot use & in destructuring patterns
if let Foo {a: &a_value, b: b_value} = x {
	panic!("THIS IS INVALID")
}

// instead, use ref:
if let Foo {a: ref a_value, b: b_value} = x {
	println!("a is {}", a_value);
}

// Thus, the same applies to match statements, where we are also destructuring
// values

let y = Some(Foo { a: 42, b: String::from("bar") });

// By default, match will copy or move matched values, depending on whether
// or not Copy is implemented:
match y {
	// y will be consumed, because we're moving f
	Some(f) => ...,
	_ => ...
}

// instead, we can use ref to indicate we only want a reference to f,
// which means that z will not be consumed
let z = Some(Foo { a: 42, b: String::from("bar") });

match z {
	// y will be consumed, because we're moving f
	Some(ref f) => ...,
	_ => ...
}
```

- `ref` allows for obtaining a reference to an _unpacked_ value
  - using `&` to attempt to get a reference while unpacking is invalid
- `ref` is _not_ an attempt to match against references - it is used to make a
  matched binding _into_ a reference
- `ref mut` is used to obtain a mutable reference to a value

## Links and resources

- [ref keyword](https://doc.rust-lang.org/1.73.0/std/keyword.ref.html)
- [Identified patterns](https://doc.rust-lang.org/1.73.0/reference/patterns.html#identifier-patterns)
