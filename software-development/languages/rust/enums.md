parent: [[+ rust]]

```rust
#[derive(Debug)]
enum TrafficLight {
    Red,
    Amber,
    Green,
}

#[derive(Debug)]
enum EnumType {
    UnitVariant,
    TupleVariant(i32, i32, i32),
    StructVariant { x: i32, y: i32 },
    EnumVariant(TrafficLight),
}

impl EnumType {
    pub fn print(self) {
        println!("{:?}", self)
    }
}

fn main() {
    let values = [
        EnumType::UnitVariant,
        EnumType::TupleVariant(1, 2, 3),
        EnumType::StructVariant { x: 1, y: 2 },
        EnumType::EnumVariant(TrafficLight::Green),
    ];

    for x in values {
        x.print();
    }
}
```

- enum variants, like structs, can be defined in a number of ways:
  - unit-like
  - as tuples that can accept arguments
  - as anonymous structs
- enums can have implementations
- `Option` and `Result` are enums that only have 2 variants
