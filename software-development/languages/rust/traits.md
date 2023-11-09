parent: [[+ rust]]

```rust
trait AppendLeet {
    fn append_boo(self) -> Self;
}

impl AppendLeet for String {
    fn append_boo(self) -> Self {
        self + "Leet"
    }
}

impl AppendLeet for i32 {
    fn append_boo(self) -> Self {
        let x = self.to_string();
        let x = x + "1337";

        x.parse().unwrap()
    }
}

fn main() {
    let x = String::from("Mr. ");
    let y = 50;

    println!("{}", x.append_boo());
    println!("{}", y.append_boo());
}
```

- traits are collections of methods that types can implement
- they are similar to interfaces in Java, and abstract classes in C++ and Python
