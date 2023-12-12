Parent: [[+ rust]]

- trait objects are [[opaque data type]]s that allow for late binding of methods 
- trait objects are defined as the `dyn` keyword followed by a set of trait bounds:
	- all traits except the first must be auto traits
	- there may not be not than one lifetime
	- opt-out bounds, e.g. `?Sized`, are not allowed
	- paths to traits may be in parens
- given the trait `Trait`, the following are all trait objects:
	- dyn Trait
	- dyn Trait + Send
	- dyn Trait + Send + Sync
	- dyn Trait + 'static
	- dyn Trait + Send + 'static
	- dyn Trait +
	- dyn 'static + Trait.
	- dyn (Trait)
- trait objects are [[Dynamically sized types]] - because the type is opaque, we don't know what type is represented, and so we don't know the size
- because trait objects are DSTs, they are used behind a pointer, e.g. `&dyn SomeTrait` or `Box<dyn SomeTrait>`
## links and resources

- https://doc.rust-lang.org/reference/types/trait-object.html