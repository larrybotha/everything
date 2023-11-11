parent: [[+ rust]]

## Implementing a single trait for a single parameter

```rust
trait TraitA {}

// x must implement TraitA - impl Trait syntax
fn do_thing_impl(x: impl TraitA) {
    // ...
}

// x must implement TraitA - trait bound syntax
fn do_thing_trait_bound<T: TraitA>(x: T) {
    // ...
}

// x must implement TraitA - `where` syntax
fn do_thing_where<T>(x: T)
where
    T: TraitA,
{
    // ...
}
```

## Implementing multiple traits for a single parameter

```rust
trait TraitA {}
trait TraitB {}

// x must implement TraitA and TraitB

// impl Trait syntax
fn do_thing_impl_trait(x: impl TraitA + TraitB) {
    // ...
}

// trait bound syntax
fn do_thing_trait_bound<T: TraitA + TraitB>(x: T) {
    // ...
}

// `where` syntax
fn do_thing_where<T>(x: T)
where
    T: TraitA + TraitB,
{
    // ...
}
```

## Implementing a single trait for multiple parameters

### Parameters where they may only be the same type

```rust
trait TraitA {}

// x and y must implement Trait A, and must be the same type

// impl Trait syntax ... not possible!
// Each parameter when using the `impl Trait` is mutually exclusive
// ...

// trait bound syntax
fn do_thing_single_type_trait_bound<T: TraitA>(x: T, y: T) {
    // ...
}

// `where` syntax
fn do_thing_single_type_where<T>(x: T, y: T)
where
    T: TraitA,
{
    // ...
}
```

### Parameters where they may be different types

```rust
trait TraitA {}

// x and y must implement Trait A, and can be different types

// imple Trait syntax
fn do_thing_multi_type_impl_trait(x: impl TraitA, y: TraitA) {
    // ...
}

// trait bound syntax
fn do_thing_multi_type_trait_bound<T: TraitA, U: TraitA>(x: T, y: U) {
    // ...
}

// `where` syntax
fn do_thing_multi_type_where<T, U>(x: T, y: U)
where
    T: TraitA,
    U: TraitA,
{
    // ...
}
```

## Links and resources

- [Rust Book: Traits as Parameters](https://doc.rust-lang.org/1.73.0/book/ch10-02-traits.html#traits-as-parameters)
