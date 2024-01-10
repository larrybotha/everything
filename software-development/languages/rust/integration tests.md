parent: [[+ rust]]

```rust
// tests/some_test_file.rs
#[test]
fn assert_the_thing() {
    assert!(true);
}
```

- integration tests go in the `[project-root]/tests` folder
- integration tests have the same level of access to source as if you were to
  add your crate to another project as a dependency

  - this supports the way that integration tests are a way of testing an
    application or library from the user's perspective
  - a side-effect of this is that only library code can be imported into
    integration tests - binaries are meant to be executed, whereas libraries
    are meant to be shared

    e.g. for a project `my_rust_project` that is compiled to a binary, the
    following would result in a compile error:

    ```rust
    //! tests/some_integration_test.rs
    use my_rust_project::main;

    #[test]
    fn dummy_test() {
        main()
    }
    ```

    `main` cannot be imported from a binary - we need to expose the testable
    aspects of the application via the library
