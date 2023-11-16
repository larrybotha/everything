parent: [[+ rust]]

```rust
// transform a vector's values
let xs = vec![1,2,3];
let xs_doubled: Vec<_> = xs.iter().map(|n| n * 2).collect();

// transform chars into String
let string = "hello";
let rot13_string: String = string.chars()
	.map(|x| x as u8)
	.map(|x| x as char)
	.collect();


// get the first error from a list of results
let results = [Ok(1), Err("oh noes"), Ok(2), Err("another")];
let result: Result<Vec<_>, &str> = results.iter().cloned().collect();

assert_eq!(result, Err("oh noes"));

// convert from a Vec of Results to a Result of Vecs
let results = [Ok(1), Ok(2), Ok(3)];
let result: Result<Vec<_>, &str> = results.iter().cloned().collect();

assert_eq!(result, Ok(vec![1,2,3]));
```

- `std::iter::Iterator::collect` can do a lot of work in transforming iterators
  into collections, and even works with types that are not typical collections,
  e.g. we can transform `Collection<Result<T>, _>` to `Result<Collection<T>, _>`
  using `collect`

## related

- [[std..iter..cloned]]

## links and resource

- https://doc.rust-lang.org/1.73.0/std/iter/trait.Iterator.html#method.collect
