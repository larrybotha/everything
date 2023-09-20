---
aliases:
  - nor
---
parent: [[+ The Lambda Calculus]]

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

## assertions

`true nor true == false`

```
   nor true true
=> ((x false) (not y)) true true
=> ((true false) (not true))
=> first false false
=> false
```

---

`true nor false == false`

```
   nor true false
=> ((x false) (not y)) true false
=> ((true false) (not false))
=> first false true
=> false
```

---

`false nor true == false`

```
   nor false true
=> ((x false) (not y)) false true
=> ((false false) (not true))
=> second false false
=> false
```

---

`false nor false == true`

```
   nor false false
=> ((x false) (not y)) false false
=> ((false false) (not false))
=> second false true
=> true
```

---