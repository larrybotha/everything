---
aliases:
  - make_pair
---
parent: [[+ The Lambda Calculus]]

```
def make_pair = λx.λy.λf.((f x) y)
```
- takes 2 arguments, and applies a function to them
## examples

### behaves similarly to `Either` in Haskell

Applying `make_pair` to [[first - the lambda calculus|first]]
```
   (((make_pair x') y') first)
=> (((λx.λy.λf.((f x) y) x') y') first)
=> ((first x') y')
=> x'
```

Applying `make_pair` to [[second - the lambda calculus|second]]

```
   (((make_pair x') y') second)
=> ...
=> y'
```

