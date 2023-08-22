parent: [[+ rust]]

```rust
// the function "foo" returns never
fn foo() -> ! {
	panic!()
}
```

- `!` is the _never_ type in Rust
- also known as _empty type_ in other languages
- useful in situations where you don't want a type returned, such as when using `continue`, which has type `!`:
	```rust
	fn main() {
		let secret_num: i32 = 5;
	
		loop {
			let mut input = String::new();
	
			// prompt for value via stdin
			std::io::stdin()
				.read_line(&mut input)
				.except("failed to read input");
	
			// try to get i32
			let guess: i32 = match input.trim().parse() {
				Ok(x) => x,
				// if we don't get i32:
				//   - continue 
				//   - which is _never_
				Err(_) => continue
			}
	
			// continue processing input 
	
		}
	}
	```

	The [[match]] statement requires that every arm returns the same type, but we have `i32` and `!` - in this special case Rust infers the return type to be `i32` because... `never` is _never_ returned!
- the definition for [[std..option..Option..unwrap]] uses `never` via `panic!`:

	```rust
	impl<T> Option<T> {
		fn unwrap(self) -> T {
			match self {
				Some(x) => x,
				None => panic!("called `Option::unwrap()` on a `None` value")
			}
		}
	}
	```

	The return type is `T` because either we get the unwrapped value, or the application crashes