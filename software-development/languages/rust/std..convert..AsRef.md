parent: [[+ rust]]

```rust
#[allow(dead_code)]
struct Person {
    name: String,
    email: String,
}

impl AsRef<Person> for Person {
    fn as_ref(&self) -> &Person {
        self
    }
}

#[allow(dead_code)]
struct Manager<'a> {
    person: Person,
    team_members: &'a Vec<Person>,
}

impl<'a> AsRef<Person> for Manager<'a> {
    fn as_ref(&self) -> &Person {
        &self.person
    }
}

fn send_email<T: AsRef<Person>>(person: &T) {
    println!("sending email to {}", person.as_ref().email);
}

fn square_generic_mut_a<T, U>(value: &mut T)
where
    // T must implement AsMut<U> - i.e. we should be able to obtain a mutable
    // reference to a type U
    T: AsMut<U>,
    // U must by some value that implements MulAssign, i.e. it can be
    // multiplied using the assignment operator. Copy is required so that the
    // compiler knows we are not attempting to _move_ x into x - it is safe to
    // make a copy of the value without additional logic
    // Note: std::ops::Mul would allow for multiplying using x * x, but
    U: std::ops::MulAssign + Copy,
{
    let x = value.as_mut();

    *x *= *x;
}

fn square_generic_mut_b<T, U>(value: &mut T)
where
    // T must implement AsMut<U>
    T: AsMut<U>,
    // U must implement Mul, where it's output is the same as its type, and must
    // also implement Copy, so that it's safe to copy the value
    U: std::ops::Mul<Output = U> + Copy,
{
    let x = value.as_mut();
    *x = *x * *x;
}

fn main() {
    let manager = Manager {
        person: Person {
            name: String::from("John"),
            email: String::from("john@example.com"),
        },
        team_members: &vec![],
    };

    send_email(&manager);

    let mut x = Box::new(5);
    let mut y = Box::new(5);

    square_generic_mut_a(&mut x);
    square_generic_mut_b(&mut y);

    assert_eq!(*x, 25);
    assert_eq!(*y, 25);
}
```

- a trait that allows for cheap reference-to-reference conversion
    * e.g. `Box<i32> => &i32`
- `AsMut` is the equivalent for a mutable reference-to-reference conversion
- `AsRef` is similar to `Into` and `From`, but for better for cheaper
    conversions. For costly conversions, prefer [[std..convert..From]]
- useful for specifying trait bounds where a type should be able to be converted
    to a reference of another type

    e.g.

    ```rust
    fn is_hello(x: impl AsRef<str>) {
        assert_eq!(x.as_ref(), "hello");
    }

    fn main() {
        is_hello(String::from("hello"));
    }
    ```

    One could think of the trait bound as _a type that can be converted to a
    reference of type T_

## links and resources

- https://doc.rust-lang.org/std/convert/trait.AsRef.html
- https://oliverjumpertz.com/blog/rusts-asref-explained/
- https://stackoverflow.com/questions/66026309/when-and-why-to-use-asreft-instead-of-t
