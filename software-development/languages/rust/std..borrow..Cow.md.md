Parent: [[+ rust]]

- Rust's implementation of [[copy-on-write]], using an enum, allowing for lazy cloning of data when mutation or ownership is required 
	- the value a `Cow` contains is either:
		- `Cow::Borrowed`, or
		- `Cow::Owned`
- can be thought of as *ownership on demand*
- `Cow` is a smart pointer that is useful for sharing data that mostly doesn't need to be mutated, but sometimes does
	- e.g. when expecting valid utf8 data that on the odd occasion requires a transformation
- `Cow` implements [[std..ops..Deref]] - properties and non-mutable methods on the contained value can be accessed directly via the `Cow`


## related

- [[std..rc..Rc]]
## links and resources

- https://www.reddit.com/r/rust/comments/v1z6bx/what_is_a_cow/
- https://deterministic.space/secret-life-of-cows.html
- https://doc.rust-lang.org/std/borrow/enum.Cow.html
- https://dhghomon.github.io/easy_rust/Chapter_42.html
- https://dev.to/kgrech/6-things-you-can-do-with-the-cow-in-rust-4l55