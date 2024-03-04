---
tags:
  - resource/video
---

Link: https://www.youtube.com/watch?v=HOSdPhAKupw
Author: [[ThePrimeagen]]

- inheritance assumes we can extract the common aspects of things into some
  parent class, and then extend that parent class. Problems arise when we have
  objects that behave exceptionally to others - we start having to perform
  backflips and write redundant code to deal with the exceptions and maintain
  inheritance
- composition can be achieved by designing features against interfaces, and then
  passing representations of entities that adhere to the interface into other
  services that know what to do with the interface, but have no knowledge of
  what the thing is that is implementing the interface - e.g. traits in Rust
- dependency injection is a way to mitigate the complexity that inheritance
  introduces, but is not a silver bullet

## links and resources

- [Faster Than Lime](https://fasterthanli.me/)
  - long-form articles often used to teach Rust
- [CodeAesthetic](https://www.youtube.com/@codeaesthetic)
  - quality views on writing code
