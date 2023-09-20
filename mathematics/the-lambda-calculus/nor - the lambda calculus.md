---
aliases:
  - nor
---

```
def nor = λx.λy.((x false) (not y))
```

## derivation

For `nor` we have

|x|y|x or y|not (x or y)|
|---|---|---|---|
|T|T|T|F|
|T|F|T|F|
|F|T|T|F|
|F|F|F|T|

i.e. `x ? false : not y`

- if the left is `true`, choose `false`
- otherwise choose the negation of the right

Therefore, using [[cond - the lambda calculus|cond]], we have:

```
λx.λy.(((cond false) (not y)) x)
```

Simplifying and reducing:

```
   (λx.λy.(((cond false) (not y)) x))
=> (λx.λy.((x false) (not y)))
```