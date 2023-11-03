parent: [[+ rust]]

```rust
use std::collections::HashMap;

// starting with an empty HashMap
let mut hash_x: HashMap<String, i32> = HashMap::new();

hash_x.insert(String::from("foo"), 3);
hash_x.insert(String::from("bar"), 2);

assert_eq!(hash_x.len(), 2);
assert_eq!(hash_x.values().sum::<i32>(), 5);

// instantiating from an iterable of tuples
let hash_y = HashMap::from([
	(String::from("foo"), 3),
	(String::from("bar"), 2),
]);

assert_eq!(hash_y.len(), 2);
assert_eq!(hash_y.values().sum::<i32>(), 5);
assert!(hash_y.contains_key(&String::from("foo)));

// inserting items into a HashMap
let some_string = "hello my string";
let mut h: HashMap<char, i32> = HashMap::new();

some_string.chars().for_each(|c| {
    h.entry(c)
        .and_modify(|count| { *count += 1; })
        .or_insert(1);
});

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

- `HashMap::entry` gets a mutable reference to the entry for a given key. This
  is somewhat analogous to [[defaultdict]] in Python
  - one can then use `.and_modify` to modify that value, if it exists
  - if the value doesn't exist, one can use `.or_insert` to provide a default
