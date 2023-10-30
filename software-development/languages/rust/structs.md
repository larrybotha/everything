parent: [[+ rust]]

```rust
struct ClassicStruct {
    x: i32,
    y: String,
    z: bool,
}

struct TupleStruct(i32, String, bool);

struct UnitStruct;

fn main() {
    let c1 = ClassicStruct {
        x: 42,
        y: String::from("foo"),
        z: true,
    };
    let c2 = ClassicStruct { z: false, ..c1 }; // functional update syntax

    let t = TupleStruct(42, String::from("foo"), true);

    let u1 = UnitStruct;
    let u2 = UnitStruct {};
}
```

- there are 3 primary ways to define structs in Rust:
  - using named fields with annotations
  - as tuples with annotations
  - as a unit, defined without a body or parameters
- _functional update syntax_ operates in a similar way to Javaascript's spread
  syntax, but is specific to structs:
  - can only be used as the terminating expression of the struct instantiation
  * fields that are not provided in the instantiation are derived from the
    struct being 'spread' into the new instance
  * update syntax doesn't appear to be available for tuple-structs
