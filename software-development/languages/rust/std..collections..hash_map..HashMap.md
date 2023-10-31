parent: [[+ rust]]

```rust
use std::collections::HashMap;

// starting with an empty HashMap
let mut hash_x: HashMap<String, i32> = HashMap::new();

hash_x.insert(String::from("foo"), 3);
hash_x.insert(String::from("bar"), 2);

assert_eq!(hash_x.len(), 2);
assert_eq!(hash_x.values().sum::<i32>(), 5);

// starting from an iterable of tuples
let hash_y = HashMap::from([
	(String::from("foo"), 3),
	(String::from("bar"), 2),
]);

assert_eq!(hash_y.len(), 2);
assert_eq!(hash_y.values().sum::<i32>(), 5);
assert!(hash_y.contains_key(&String::from("foo)));
```

- evaluating whether a `HashMap` has a key or not is similar to using `in` in
  Python, and `Object.hasOwnProperty` in Javascript

  Python:

  ```python
  my_dict = {"foo": 2}

  assert "foo" in x, "foo not in x"
  ```

  Javascript:

  ```javascript
  const x = {"foo": 2};'

  assert(x.hasOwnProperty("foo"), "foo not in x");
  ```

  Rust:

  ```rust
  let my_dict = HashMap::from([("foo", 2)]);

  assert!(my_dict.contains_key(&"foo"));
  ```
