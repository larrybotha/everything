Parent: [[+ rust]]

- an enum error type for errors that can never happen
- useful for indicating that a result is always `Ok`
    e.g for a conversion from `T` to `U` using `TryFrom`:

    * if `U` implements `Into<T>`, then `T::try_from<U>` _always_ returns
        `Ok(U::into<T>)`
    * `T::try_from<U>` therefore returns `Result<T, Infallible>`

    If we had to implement `TryFrom<i32> for f32`, we could also have an
    implementation of `Into<f32> for i32` which would guarantee that an integer
    is converted to a floating point number

    With this guarantee, `TryFrom<i32> for f32` would _always_ return a value
    which could be converted back to an `f32`

## related

- [[std..convert..TryFrom]]

## links and resources

- https://doc.rust-lang.org/std/convert/enum.Infallible.html
