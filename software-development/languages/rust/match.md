parent: [[+ rust]]

- pattern matching on values, similar to `switch` in JavaScript, and `match` in Python
- every arm must return the same type
- `match` doesn't perform automatic referencing and dereferencing as evaluating
  a value in an `if` condition does. `match` requires one to be explicit:

  ```rust
  let x = String::from("hello"); // &str

  // `if` automatically references String to &str when using condition
  let y = if x == "hello" { "ok" } else { "nok" };

  // match requires us to convert String to &str ourselves
  let z = match &x[..] {
  	"hello" => "ok",
  	_ => "nok"
  };
  ```
