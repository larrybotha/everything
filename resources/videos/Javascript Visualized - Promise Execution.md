---
tags:
  - resource/video
---

Link: https://www.lydiahallie.com/blog/promise-execution
Author: [[Lydia Hallie]]

## takeaways

- describes how the event loop is comprised of the task queue and microtask queue
- describes how Promise Reactions are involved in scheduling of work to be done
- shows how items added to the call stack have higher priority than those in the
  microtask queue - [[ThePrimeagen]] describes in some video how chaining
  `.then` can impact performance because every thenable has to wait for the
  stack to clear before being processed - this is demonstrated nicely in this
  video
