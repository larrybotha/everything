Parent: [[+ rust]]

```rust
use std::fs::rename;
use std::io::{stdout, Write};
use std::path::Path;

fn main() {
    let data = ["a.txt", "b.text", "c.txt"];
    // Try write each path to stdout
    let result = data.iter().try_for_each(|x| writeln!(stdout(), "{}", x));

    assert!(result.is_ok());

    let mut iterator = data.iter().cloned();
    // Try rename each path
    // If this fails, the iterator short-circuits...
    let result = iterator.try_for_each(|x| rename(x, Path::new(x).with_extension("old")));

    assert!(result.is_err());

    // and we can continue iterating over the remaining items
    assert_eq!(iterator.next(), Some("b.text"));
}
```

- used for applying a fallible function to each item in an iterator, i.e.
    something that returns a `Result<T, E>`
- the fallible version of `Iterator::for_each`
- the stateless version of `Iterator::try_fold`

## links and resources

- https://doc.rust-lang.org/1.74.1/std/iter/trait.Iterator.html#method.try_for_each
