parent: [[+ rust]]

- a method in the standard library available on `Option` and `Result`
- works similarly to `flatmap` in other languages
```rust
fn wrap<T>(value: i32) -> Option<i32> {
	Some(value)
}

let x: Option<i32> = Some(5);

// manually unwrap the value
x
	.map(|n| wrap(n)) // here we return Option<Option<i32>>
	.unwrap_or(None)  // unwrap the value, so that we're back to Option<i32>

x.and_then(|n| wrap(n)) // no need to unwrap
```
