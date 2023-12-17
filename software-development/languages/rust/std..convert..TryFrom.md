Parent: [[+ rust]]

```rust
#[derive(Debug)]
struct Car {
    brand: String,
}

impl TryFrom<String> for Car {
    type Error = &'static str;

    fn try_from(brand: String) -> Result<Car, Self::Error> {
        match brand {
            x if x.is_empty() => Err("empty string not allowed"),
            x => Ok(Car { brand: x }),
        }
    }
}

impl From<Car> for String {
    fn from(car: Car) -> String {
        car.brand
    }
}

fn main() {
    let invalid_car = Car::try_from("".to_string());
    let valid_car = Car::try_from("some_brand".to_string());

    println!("{:?}", invalid_car);
    println!("{:?}", valid_car);

    assert_eq!(invalid_car.unwrap_err(), "empty string not allowed");

    let brand = String::from(valid_car.unwrap());

    println!("brand is {:?}", brand);

    assert_eq!(brand, "some_brand".to_string());
}
```

- allows for safe conversions where a type may or may not convert to another
    type

    e.g. `f32` -> `i32`: how does one handle the decimal place if it isn't 0?
    Round up, round down, truncate the decimal... something else...?

    `::try_from` allows for one to explicitly handle the case where the
    conversion fails
- the return type of `::try_from` is `Result<T, E>` - either the conversion
    succeeds, or it fails

## related

- [[std..convert..From]]

## links and resources

- https://doc.rust-lang.org/std/convert/trait.TryFrom.html
