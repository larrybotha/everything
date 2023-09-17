---
aliases:
  - first
---
parent: [[+ The Lambda Calculus]]

```
def first = λx.λy.x
```
## examples

```
   ((first id) apply)
=> ((λx.λy.x id) apply)
=> (λy.(id) apply)
=> id
```