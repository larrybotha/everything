parent: [[+ rust]]

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
