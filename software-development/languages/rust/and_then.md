parent: [[+ rust]]

- a method in the standard library available on `Option` and `Result`
- works similarly to `flatmap` in other languages

```rust
fn wrap<T>(value: i32) -> Option<i32> {
	Some(value)
}

let x: Option<i32> = Some(5);

// we can use unwrap_or _after_ mapping
x
	// here we return Option<Option<i32>>
	.map(|n| wrap(n))
	// unwrap the value, so that we're back to Option<i32>
	.unwrap_or(None);

// or
// .and_then, which is syntactic sugar for the above
x.and_then(|n| wrap(n));
```
