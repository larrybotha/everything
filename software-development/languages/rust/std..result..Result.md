parent: [[+ rust]]

- `Result` is a more specialised version of the `Option` type, which allows the
  application to return information to the user indicating why there is no
  value, i.e. via an `Error` message
- a custom `Result` is defined using the following signature:

  `Result<OkType, ErrorType>`

  e.g.

  ```rust
  enum HttpErrorStatus {
    400,
    401,
    // ...
  }

  type ResponseResult = Result<Json, HttpErrorStatus>;
  ```

- functions that return `Result` are short-circuitable using the `?` syntax when
  accessing a wrapped value

  ```rust
  use std::num::ParseIntError;

  fn square_string_int_verbose(x: &str) -> Result<i32, ParseIntError> {
      let value = x.parse::<i32>();

      match value {
          Ok(n) => n * n,
          Err(e) => Err(e),
      }
  }

  fn square_string_int_terse(x: &str) -> Result<i32, ParseIntError> {
      let value = x.parse::<i32>()?; // short-circuit and return Err if Err

      Ok(value * value)
  }

  fn square_string_int_terser(x: &str) -> Result<i32, ParseIntError> {
      x.parse::<i32>()
	      .map(|value| value * value)
  }
  ```

## Links and resources

- [[question mark operator|?]]
- [Other uses of `?`](https://doc.rust-lang.org/stable/rust-by-example/error/multiple_error_types/reenter_question_mark.html)
- https://doc.rust-lang.org/std/result/