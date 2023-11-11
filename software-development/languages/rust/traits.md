parent: [[+ rust]]

```rust
//
https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=62dcbbd97fa7129f9ff66ccc39e20701

trait AppendLeet {
    // can be optionally overridden
    fn shout(&self) {
        println!("RAWR")
    }

    // must be provided
    fn append_leet(&self) -> Self;
}

impl AppendLeet for String {
    fn append_leet(&self) -> Self {
        self.to_owned() + "Leet"
    }
}

impl AppendLeet for i32 {
    fn append_leet(&self) -> Self {
        let x = self.to_string();
        let x = x + "1337";

        x.parse().unwrap()
    }
}

fn main() {
    let x = String::from("Mr. ");
    let y = 50;

    println!("{}", x.append_leet());
    println!("{}", y.append_leet());

    x.shout();
    y.shout();
}
```

- traits are collections of methods that types can implement
- they are similar to interfaces in Java, and abstract classes in C++ and Python
- see [[traits as parameters]] for mechanisms for defining bounds for parameters
  to functions
