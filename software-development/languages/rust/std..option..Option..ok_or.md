parent: [[+ rust]]

```rust
fn main() {
    let xs = vec![0, 1, 2];

    let result = xs.iter()
      .next()
      .filter(|&x| x > &0)
      .ok_or("ermagerd!");

    assert_eq!(result, Err("ermagerd!"));
}
```

- eagerly converts `Option<T>` to a `Result<T, E>`
- favour using `Option::ok_or_else` over this method - the `...or_else` versions of transformers only execute the callback when they explicitly need to:

	```rust
	fn main() {
	    let value: Option<usize> = Some(1);
	
	    let result = value.ok_or({ println!("value is not Some!"); 0 });

		// this holds, but "value is not Some!" was printed
	    assert_eq!(result, Ok(1));
	}
	```

## links and resources

- https://doc.rust-lang.org/1.74.0/std/option/enum.Option.html#method.ok_or
- https://stackoverflow.com/questions/45547293/why-should-i-prefer-optionok-or-else-instead-of-optionok-or
- https://medium.com/@techhara/rust-tip-and-trick-2-5a92641191f6
