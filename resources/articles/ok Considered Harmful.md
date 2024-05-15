---
tags:
  - resource/article
---

Link: https://www.dolthub.com/blog/2024-05-10-ok-considered-harmful/

## Takeaways

- prefer `xExists` for map lookups rather than `ok`
- for functions where an error can be considered separately from a falsy return,
  return both values, mitigating the user from having to determine whether a
  single falsy value is an error or not
- using `ok` for type assertions is a convention which is harmless enough to
  continue using

## related

- [[+ golang]]
