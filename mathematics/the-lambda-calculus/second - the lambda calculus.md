---
aliases:
  - second 
---
parent: [[+ The Lambda Calculus]]

```
def second = λx.λy.y
```
## examples

```
   ((second id) apply)
=> ((λx.λy.y id) apply)
=> (λy.y apply)
=> apply
```