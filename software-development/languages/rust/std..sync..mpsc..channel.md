parent: [[+ rust]]

```rust
// demo at https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=f994113249f18c817cce6f9ae6a22075
use std::sync::mpsc;
use std::thread;

fn main() {
    // transmitter and receive
    let (tx, rx) = mpsc::channel();

    // spawn a thread from which messages can be sent
    thread::spawn(move || {
        println!("sending message from thread...");
        let my_string = "foobar";

        // the sender is moved into 
        // this closure
        // .send takes ownership of
        // 'my_string' - the value
        // may be manipulated in 
        // another thread, so we need 
        // ownership transferred away
        // from this thread
        tx.send(my_string).unwrap();
    });

    // receive the message
    let message = rx.recv().unwrap();

    println!("Message received: {}", message);
}
```

- channels are a concept in programming that allow for data to be sent across
  threads
- a channel always has a transmitter / sender and a receiver - the relationship
  can be thought of like a river
  - the transmitter sits upstream, sending data
  - the receiver sits downstream, checking to see if any data has been sent
- a channel is considered closed if either the sender or receiver are dropped
- `.send` and `.recv` both return `Result` - attempting to send or receive on a
  closed channel will result in an error
- `.send` takes ownership of the values of sends - another thread may use the value, so for safety Rust ensures that the thread where the value is sent is not allowed to access the value once it is sent
- in [Go's documentation on concurrency](https://go.dev/doc/effective_go#concurrency)
  they recommend:

      _Do not communicate by sharing memory; instead, share memory by
      communicating._

  This is similar to emitting events in the DOM as opposed to React where data
  is passed around explicitly everywhere via closures

## Related

- [[std..thread..JoinHandle..join]]

## Links and resources

- https://doc.rust-lang.org/book/ch16-02-message-passing.html
- https://go.dev/doc/effective_go#concurrency
- 
