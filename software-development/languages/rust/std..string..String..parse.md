parent: [[+ rust]]

```rust
use std::num::ParseIntError;

fn maybe_square(x: &str) -> Result<i32, ParseIntError> {
    x.parse::<i32>().map(|v| v * v)
}
```

- attempts to parse a string to the given type, returning a [[std..result..Result]]
- works similarly to Javacript's `Number.parseInt`, and Python's `int`

  - Javascript:

    ```javascript
    	const value: number | NaN = Number.parseInt("42");
    ```

  - Python:

    ```python
    try:
    	value = int("42")
    except ValueError:
    	raise
    ```
