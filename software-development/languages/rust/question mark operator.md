---
aliases:
	- ?
---

parent: [[+ rust]]

```rust
use std::cmp::Ordering;
use std::error;
use std::fmt;

// main could return one of two types of error:
//  - ParseIntError, or
//  - NumberError
//
// NumberError does not implement Error, but the question mark operator
// calls From::from under the hood, coercing the value into
// Box<dyn error::Error>
//
// This allows us to indicate that we're getting _some_ type of value that
// implements error::Error, without having to implement Error
fn main() -> Result<(), Box<dyn error::Error>> {
    let user_input = "42";
    let value = user_input.parse::<i32>()?; // could raise ParseIntError
    let value = evaluate(&value)?; // could raise NumberError

    println!("got a non-zero positive value: {}", value);

    Ok(())
}

fn evaluate(x: &i32) -> Result<&i32, NumberError> {
    match x.cmp(&0) {
        Ordering::Less => Err(NumberError::LtZero),
        Ordering::Equal => Err(NumberError::Zero),
        Ordering::Greater => Ok(x),
    }
}

// In order for NumberError to be coerced into error::Error, we need to
// implement:
//  - Debug
//  - Display
//  - error::Error
#[derive(Debug)]
enum NumberError {
    LtZero,
    Zero,
}

// This gives us NumberError::from, which when called by the ? operator coerces
// our errors into Box<dyn error::Error>
impl error::Error for NumberError {}

impl fmt::Display for NumberError {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        let description = match *self {
            NumberError::LtZero => "number is negative",
            NumberError::Zero => "number is zero",
        };

        f.write_str(description)
    }
}
```

- the `?` operator calls `From::from` under the hood, coercing values into
  `Box<dyn error:Error>`
  - in order for this coercion to happen, the type must implement `error::Error`
  - implementing `error::Error` comes with additional requirements, which can
    be seen by evaluating [`error::Error`s trait definition](https://doc.rust-lang.org/1.73.0/std/error/trait.Error.html)
    - both `Display` and `Debug` must be implemented so that errors can be
      rendered
- `Box<dyn error::Error>` shouldn't be used by library code - it prevents users
  from evaluating specific issues. All they know is that _something that
  implements error::Error_ was returned
  - instead, define custom errors

## Links and resources

- [Other uses of `?`](https://doc.rust-lang.org/stable/rust-by-example/error/multiple_error_types/reenter_question_mark.html)
- [[dyn]]
