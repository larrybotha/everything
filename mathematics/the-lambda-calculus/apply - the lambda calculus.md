---
aliases:
  - apply
---
parent: [[+ The Lambda Calculus]]

```
def apply = λf.λx.(f x)
```

- applies a function `f` to an argument `x`, as with JavaScript's `apply`
- `apply` adds a layer of [[β reduction]] to an application - i.e. one could use `apply` for partial application

e.g. 

```
   (apply id)
=> (λf.λx.(f x) id)
=> λx.(id x)
=> id
```

## Examples

Use [[apply - the lambda calculus|apply]] to apply [[identity - lambda calculus|identity]] to [[self-application - the lambda calculus|self_apply]]:

```
   ((λf.λx.(f x) id) s_apply)
=> (λx.(id x) s_apply)
=> (id s_apply)
=> s_apply
=> λs.(s s)
```