parent: [[+ rust]]

```rust
use std::num::ParseIntError;

#[derive(Debug)]
enum ErrorWrapper {
    ParseInt(ParseIntError),
    DivideByZero,
}

impl ErrorWrapper {
    fn from_parseint(x: ParseIntError) -> ErrorWrapper {
        ErrorWrapper::ParseInt(x)
    }

    fn from_zero_division() -> ErrorWrapper {
        ErrorWrapper::DivideByZero
    }
}

fn safe_divide(x: i32, y: &str) -> Result<i32, ErrorWrapper> {
    let y = y.parse().map_err(ErrorWrapper::from_parseint)?;

    match y {
        0 => Err(ErrorWrapper::from_zero_division()),
        n => Ok(x / n),
    }
}

fn main() -> Result<i32, ErrorWrapper> {
    let user_input = "0";
    let result = safe_divide(42, user_input);

    result
}
```

- `Result::map_err` allows one to map an error to another error
- `Result::map_err` is short-circuitable, because it is returning a `Result`
