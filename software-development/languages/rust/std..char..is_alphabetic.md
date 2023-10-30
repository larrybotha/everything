parent: [[+ rust]]

```rust
fn main() {
	let x = 'a';
}

if x.is_alphabetic() {
	println!("x is alphabetic");
} else if x.is_numeric() {
	println!("x is alphabetic");
} else if x.is_whitespace {
	println!("x is whitespace");
} else {
	println!("x is something else!");
}
```

- `std::char` has a number of predicates for evaluating characters and
  determining what type of character is held by a variable
