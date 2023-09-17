---
aliases:
  - not
---

```
def not = λx.((x false) true)
```

## derivation

`not` has the following truth table:

|x|not x|
|---|---|
|T|F|
|F|T|

- `not` is unary, and resolves to either [[booleans - the lambda calculus|true]] or [[booleans - the lambda calculus|false]]
- [[cond - the lambda calculus|cond]] returns one of two values given a condition

Thus, we have:

```
   (λx.((cond false) true) x)
=> (λx.((
     λe1.λe2.λc.(
       (c e1) e2) false) true
     ) x
   )
=> (λx.(
       λc.((c false) true)
     ) x
   )
=> ((x false) true)
```