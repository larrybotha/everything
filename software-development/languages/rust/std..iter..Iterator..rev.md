parent: [[+ rust]]

```rust
let xs = [1,2,3];

for x in xs.iter().rev() {
	println!("{}", x);
}

// 3
// 2
// 1
```

- iterates over `xs` in reverse
- mitigates having to mutate the original value
- only available on types that are double-ended, e.g. will not work on an
  infinite range
