---
tags:
  - resource/article
---

Link: https://akavel.com/go-errors

- instead of returning only the plain error that was returned from
  some failed instruction, add context by returning a new error that
  appends the original error
- similar to using `raise(MyExc) from exc` in Python

# related

- [[+ golang|Golang]]
