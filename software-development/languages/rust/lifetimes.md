parent: [[+ rust]]

- whenever one sees a lifetime parameter, the reference that that parameter
  applies to should be read as:

  > **x must live _at least_ as long as 'a**

  e.g.

  ```rust
  // x:
  //    - is a reference to an i32, and
  //    - must live _at least_ as long as 'a
  fn do_something_with_ref<'a>(x: &'a i32) {
      // ...
  }
  ```

- lifetime parameters don't change lifetimes of values / references - they
  indicate to the compiler to reject any code where a value being passed into
  the function or struct does not adhere to the constraints
- the scope of where values are defined determines their ch10-03-lifetime-syntax

  e.g. the following will fail because `result`, after the `bar` scope, could be
  holding a dangling reference:

  ```rust
  fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
      if x.len() > y.len() {
          x
      } else {
          y
      }
  }

  fn main() {
      let foo = String::from("pew");
      let result;

      {
          let bar = String::from("pew pew pew");
          result = longest(foo.as_str(), bar.as_str());
      } // bar is dropped here

      // result now holds what _may_ be a dangling reference - this violates
      // borrowing rules, and will cause a compiler error

      println!("longest: {result}");
  }
  ```

  So... the values that are passed into `longest` must live _at least as long_
  as the value assigned to `result` - `bar` violates this - it is dropped before
  `result` is dropped

- lifetime parameters in structs indicate to the compiler which values in the
  struct must have lifetimes _at least_ as long as the lifetime of the struct

      ```
      // field x's value must live at least as long as Foo
      struct Foo<'a> {
      	x: &'a Bar
      }

         Foo { x }

            ├―――――――――――――――――――――――――――――――――――――――――――▶

      	 x

      1: ├―――――――――――――――――――――――――――――――――――――――――――――――――――――▶
      2:         ├―――――――――――――――――――――▶
      3: ├―――――――――――――――――――――――――――――▶
      ```

      1. safe: if x is dropped, Foo will already have been dropped, and all
         references removed
      2. impossible: Foo can't be instantiated without x existing
      3. dangling reference: if x is dropped before Foo is dropped, we'll have a
         dangling reference - a reference to a value that no longer exists

- lifetime bounds in functions are required when the function accepts more than
  one reference, and returns one of them... the compiler needs to know which
  lifetime will be returned to ensure that neither of the values the
  references point to will be dropped before the function is done:

  ```rust
  // `either` may return x or y - both values must live _at least_ as long as 'a
  fn either<'a>(x: &'a i32, y: &'a i32) -> &'a i32 {
      // ...
  }

  // `second` may _only_ return y
  // x must live _at least_ as long as 'a
  // y must live _at least_ as long as 'b
  fn second<'a, 'b>(x: &'a i32, y: &'b i32) -> &'a i32 {
      // ...
  }
  ```

## Links and resources

- [Validating references with lifetimes](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html)
