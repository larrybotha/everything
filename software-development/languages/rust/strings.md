parent: [[+ rust]]

```rust
let string_slice1 = "foo";					      // &str
let string_slice2: &str = "foo".into();		// &str
let string1 = String::from("bar");	      // String
let string2 = "bar".to_string();		      // String
let string3: String = "bar".into();	      // String

assert_eq!("foo", string_slice1.to_string().as_str());
assert_eq!(String::from("bar"), string1.as_str().to_string());

// concatenation via addition
let x = "foo";
let y = "bar";
let xy = x.to_string() + y;

assert_eq!(xy, "foobar");

// concatenation via format!
let x = "foo";
let y = "bar";
let xs = format!("{}{}", x, y);

assert_eq!(xy, "foobar");

// concatetation via mutation with String::push
let mut x = "foo".to_string();
let y = "bar";

y.chars().for_each(|c| x.push(c));

assert_eq!(x, "foobar");

// concatetation via mutation with String::push_str
let mut x = "foo".to_string();
let y = "bar";

x.push_str(y);

assert_eq!(x, "foobar");

// get an iterator by splitting a string at newlines
let string_iter = "hello\nthere".lines();
```

- `&str` is allocated on the heap, and is constant for the duration of the
  application's lifetime - these values are hard-coded into the executable
  - slices are references to arrays. `&str` is actually `&[u8]` - a slice of an array of u8 values
  - similar to how `&[T]` is a view into `Vec[T]`, so too could a `&str` be a view into a `String`
- `String` is dynamic, unlike `&str`, and is thus growable and mutable. `String`
  values are pushed to the stack
- `String::as_str` and `&str::to_string` are isomorphic operations

## Links and resources

- [[std..string..String]]
- http://doc.rust-lang.org/1.73.0/book/ch04-01-what-is-ownership.html#the-stack-and-the-heap
