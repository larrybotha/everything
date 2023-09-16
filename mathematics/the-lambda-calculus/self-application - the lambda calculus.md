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

```
   (λs.(s s) λs.(s s))
=> (λs.(s s) λs.(s s))
```

- not all expressions terminate in lambda calculus