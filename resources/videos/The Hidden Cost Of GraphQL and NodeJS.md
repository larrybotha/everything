---
tags:
  - resource/video
---

Link: https://www.youtube.com/watch?v=i0YfiQlzv6M
Author: [[ThePrimeagen]]

- `await`ing on calls has a direct impact on the event loop - after a promise
  resolves, it is appended to the event loop
  - if we are chaining `.then`, then every intermediately resolved promise is
    pushed onto the end of the event loop
- callbacks are synchronous - they will block the event loop until they are done
  executing - i.e. they are not deferred to the end of the event loop once
  they are done doing their work
- it's incredibly easy to allocate tons of memory in JavaScript
