parent: [[+ rust]]

- a `Mutex` acts like a lock / key, allowing one to protect data from being
  modified while the lock is active

  - e.g. there are a bunch of kids, there is a malleable clay toy, and there
    is a key associated with that toy.

    - one of the children picks up the toy and the key, and they are allowed
      to play with the toy, and make modifications to it
      ```rust
      let mut toy = toy.lock().unwrap();
      ```
    - no other child may play with the toy while that child has the key
    - when the child is done with the toy, another child may take the key

      ```rust
      {
      // child a takes the toy
      	let mut locked_toy = toy.lock().unwrap();
      	// child a makes modifications
      } // lock goes out of scope and is dropped

      // child b takes the toy
      // ...
      ```

- a `Mutex` becomes _poisoned_ when

  - a thread holding a lock panics, and
  - that thread doesn't release the lock

  e.g. a child with the toy starts freaking out, an adult comes along to soothe
  the child and takes them away, but the child continues to hold onto the toy, not
  allowing the other children to play with it

## Links and resources

- [Official Rust docs for std::mpsc::Mutex](http://doc.rust-lang.org/1.72.1/std/sync/struct.Mutex.html)