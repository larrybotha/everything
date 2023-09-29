---
aliases:
  - self_apply
---
parent: [[+ The Lambda Calculus]]

```
def self_apply = λs.(s s)
```

- applies its argument to itself
- related to recursive functions

## can be derived from [[apply - the lambda calculus|apply]]

```
   ((apply s) s)
=> ((λf.λx.(f x) s) s)
=> (λx.(s x) s)
=> (s s)
```
## does not terminate

Or, worded differently, is self-replicating

```
   self_apply self_apply
=> (λs.(s s) self_apply)
=> self_apply self_apply
=> ...
```

- not all expressions terminate in lambda calculus