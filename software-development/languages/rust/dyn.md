parent: [[+ rust]]

```rust
// print things that have implemented Debug
fn print_debug(x: &dyn Debug) {
    println!("{:?}", x);
}
```

- `dyn SomeTrait` can be read as _"any type that implements `SomeTrait`"_
- `dyn` accepts a _trait_ as an argument - _not_ structs, enums, etc.
- this is _dynamic dispatch_ - the compiler determines at run-time which method
  is appropriate to call based on the type of value
- pros and cons:
  - pros:
    - one doesn't need to implement a separate method / function for each
      type that is operated on - as long as the type passed in implements the
      `Trait`, the function is callable on that value
      - this may lead to a smaller compiled executable
  - cons:
    - there is a level of indirection that `dyn` introduces, which results in a
      run-time cost
      - this is because the compiler cannot rely on the type to determine which
        functions or methods are callable on the value - it has to evaluate a
        _vtable_, i.e. a table that is managed which maps function calls to
        pointers
    - methods called by dynamic dispatch generally cannot be inlined by the
      compiler

## Links and resources

- https://doc.rust-lang.org/1.73.0/std/keyword.dyn.html
