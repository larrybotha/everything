parent: [[+ rust]]

```rust
mod math {
    // make addition::add available as math::aliased_add from outside
    // of the module
    pub use self::addition::add as aliased_add;

    mod addition {
        pub fn add(x: i32, y: i32) -> i32 {
            let (x, y) = if x > y { (y, x) } else { (x, y) };

            recursive_add(x, y)
        }

        // recursive_add is only visible inside module
        fn recursive_add(x: i32, y: i32) -> i32 {
            if x == 0 || y == 0 {
                x + y
            } else {
                recursive_add(x + 1, y - 1)
            }
        }
    }
}

fn main() {
    // math::addition is private - we can't access any of its values directly
    // println!("sum of 3 and 2: {}", math::addition::add(3, 2));
    println!("sum of 3 and 2: {}", math::aliased_add(3, 2));
}
```

- values inside modules are made available outside the module using the `pub`
  keyword
- values inside modules can be exposed with aliases using
  `use self::{value} as [alias]`. Public values inside private modules can be
  exposed this way
