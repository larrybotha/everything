parent: [[+ rust]]

```rust
#[cfg(test)]
mod tests {
    fn do_setup() {
        // ...
    }

    #[test]
    fn do_the_assert_dance() {
        do_setup();

        assert!(true);
    }
}
```

- test blocks are defined with `#[cfg(test)]` attribute above a `mod tests`
  module
- functions that are run as tests require the `#[test]` attribute
- setup functions can be defined without the `#[test]` attribute

## related

- [[attributes]]
