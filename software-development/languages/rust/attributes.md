parent: [[+ rust]]

```rust
// attribute applied to the enclosing module or create
#![crate_type = "lib"]

// marking a function as a unit test
#[test]
fn test_the_thing() {
    // ...
}

// conditional compilation
#[cfg(target_os = "linux")]
mod linux_only {
    // ...
}
#[cfg(target_os = "windows")]
mod windows_only {
    // ...
}

// suppress warning/error messages
#[allow(non_camel_case_types)]
#[allow(dead_code)]
type int8_t = i8;

// enforce errors, scoped to a function / module etc.
#[allow(dead_code)]
fn error_on_unused_vars() {
    #![allow(unused_variables)]

    let x = 5;
}
```

- attributes define individual pieces of metadata for crates, libraries,
  modules, structs, functions, lifetimes, etc. - see docs
- `cfg` and `cfg_attr` allow for conditional compilation and inclusion of
  attributes

## Links and resources

- [Attributes: Rust book](https://doc.rust-lang.org/1.73.0/reference/attributes.html)
