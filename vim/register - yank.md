---
aliases:
  - yank register
---

%%
parent:: [[+ vim]]
%%

The yank register, `"0`, is only populated by yank motions, as opposed to the [[register - unnamed|unnamed register]]. It is stable across edits, until we yank something else

Using `x`, `s`, `d{motion}`, or `c{motion}` have no effect on this register

Inspect with

```vim
:reg "0
```