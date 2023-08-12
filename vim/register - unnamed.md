---
aliases:
  - unnamed register
---

%%
parent:: [[+ vim]]
%%

The default register, populated by all of the following:

- `x`
- `s`
- `d{motion}`
- `c{motion}
- `y{motion}`

It is volatile and unstable - prefer using named registers if you need stability when accessing items from the register, or the [[register - yank|yank register]] if you're interested in only the last yanked item