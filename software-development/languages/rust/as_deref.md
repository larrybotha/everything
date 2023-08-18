parent: [[+ rust]]

```rust
let x = Some(Box::new(5));

assert_eq!(x.as_deref(), Some(&5));
//        [    1    ]   [    2    ]
// 1 - Some(&i32) - we have dereferenced from Box<i32> to &i32
// 2 - also Some(&str)

let y: Option<String> = Some("foo".to_owned());

// assert that we have &str after we deref
assert_eq!(y.as_deref(), Some("foo"));
//         [    1    ]   [    2    ]
// 1 - Some(&str) - we have dereferenced from String to &str
// 2 - also Some(&str)
```

- converts `Option<T>` to `Option<&T::Target>` where `::Target`
  represents dereferencing of a contained value via `Deref`,
  such as when the `Option` contains a pointer type such as
  `[[stdrcrc]]` or `[[stdboxedbox]]`
