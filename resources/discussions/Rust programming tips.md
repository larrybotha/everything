---
id: "Rust programming tips"
aliases:
	- "The Rust programming language absolutely positively sucks"
tags: 
  - resource/discussion 
---

Link: https://www.reddit.com/r/rust/comments/12b7p2p/the_rust_programming_language_absolutely/jevs1h7

## Takeaways

- write Rust in a dumb way before attempting to optimise, if you even need to
- don't write multi-threaded code until you've got a single-threaded PoC working. If you need multi-threading afterwards, use `tokio` or `rayon`
- start by cloning everything first, and only then attempt to get lifetimes to work

## Summary

> in general, Rust highly encourages clear ownership of data throughout your program, and discourages mutability as much as possible.
>
> I would also suggest writing your program in the "dumbest" way you can first, and performance optimise it later. Because of Rust's compile time guarantees and really elegant testing (using `cargo test` and benchmarking with `criterion`), it's really easy to modify a Rust program.
>
> - Multithreaded? Don't bother. Write the single threaded version first, and use either `tokio` or `rayon` to add multithreading afterwards.
> - Caching? Too hard. You can use `.prepare_cached` as [u/zuurr](https://www.reddit.com/user/zuurr/) once it's working.
> - Bit-packing booleans for minimal memory usage? Just waste the RAM now and make a more efficient version later.
> - Lifetimes not working? Just clone the data, and don't bother with a reference. Deriving the `Clone` trait is one line of code (usually) and is surprisingly fast.
> - Compile times too slow? Yeah not much you can really do about that. I'd suggest using `cargo check` to minimise your issues, but sadly the Rust compiler does a lot of work on each compilation.

## References

- [[+ rust]]
