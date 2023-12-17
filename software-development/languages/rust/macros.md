---
aliases:
- macro
---

parent: [[+ rust]]

- macros are how Rust achieves metaprogramming - code that writes other code
- macros are allowed to be variadic, on contrast to functions in Rust which have to be defined with an explicit number of arguments, e.g. `println!`
- generally more difficult to read and understand - you have to write Rust that writes Rust
- Rust has two primary types of macros:
  - declarative, for general metaprogramming
  - procedural, which are further divided into
    - macros that operate like `#[derive]`
    - macros that define custom attributes that can be applied to items
    - function-like macros which operate on their arguments (like decorators...?)
- custom macros are defined using `macro_rules!`
  - the body of declarative macros operate like [[match]] expressions
  - macros _must_ be higher in the code than where they are used, i.e. they do
    not benefit from anything like the hoisting behaviour in Javascript
- custom macros defined inside modules need to be explictly marked as being
  exported from the module:

    ```rust
      mod macros {
      		macro_rules! my_macro {
      				() => {
      						println!("Check out my macro!");
      				};
      		}
      		// make this macro available outside of the module
      		pub(crate) use my_macro;
      }

      fn main() {
      		use macros::my_macro;

      		my_macro!();
      }
      ```

- macros may be defined with overrides, e.g. to allow for variadic arguments:

  ```rust
  // https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=5dc32bce5fe4701f1382c5a6aaea982d
  macro_rules! thinger {
    () => { println!("no arguments!") };
    ($val:expr) => { println!("got this value: {}", $val) };
    ($val:expr, $($vals:expr ),+) => {{
      thinger! { $val }
      thinger! { $($vals),+ }
    }}
  }

  fn main() {
    thinger!();
    thinger!(42);
    thinger!(1, 2, 3);
  }
  ```

## Related

- [The Little Book Of Macros](https://danielkeep.github.io/tlborm/book/index.html)
- https://veykril.github.io/tlborm/
- https://doc.rust-lang.org/rust-by-example/macros/variadics.html
- Decorators using macros: https://dev.to/sbalasa/reimagining-python-decorators-with-rust-macros-a-powerhouse-combination-19aj