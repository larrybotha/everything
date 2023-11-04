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

- there are a few ways of preventing values in `match` statements from being
  consumed, depending on type of value:

  - destructure the reference:

    ```rust
    #[derive(Debug)]
    struct Foo(i32);

    let x = Some(Foo(42));

    // match on a reference to x
    match &x {
      Some(f) => println!("got {:?}", f),
      _ => println!("got nothing!"),
    }

    x; // x has not been moved
    ```

  - use the `ref` keyword to indicate in the branch that we only want a
    reference to the contained value:

    ```rust
    #[derive(Debug)]
    struct Foo(i32);

    let x = Some(Foo(42));

    match x {
      // make the matched binding 'f' a reference
      Some(ref f) => println!("got {:?}", f),
      _ => println!("got nothing!"),
    }

    x; // x has not been moved
    ```

    see [[ref]]
