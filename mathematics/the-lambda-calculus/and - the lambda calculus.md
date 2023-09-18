---
aliases:
  - and
---

```
def and = λx.λy.((x y) false)
```

## derivation

For `and` we have

|x|y|x and y|
|---|---|---|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|F|

i.e. `x ? y : false`

- if the left is `true`, choose the right
- otherwise choose `false`

Therefore, using [[cond - the lambda calculus|cond]], we need the following outcome:
```
   λe1.λe2.λc.((c e1) e2)
   #            x y   F
```

So, if we apply [[cond - the lambda calculus|cond]] to the arguments in the same order, and then reduce:
```

   λx.λy.((((cond) y) false) x)
=> λx.λy.(((
     λe1.λe2.λc.((c e1) e2) 
     y) false) x)
=> λx.λy.((x y) false)
```
## assertions

`true and true == true`

```
   ((and true) true)
=> ((λx.λy.((x y) false) true) true)
=> ((true true) false)
=> ((first true) false)
=> true
```
---

`true and false == false`

```
   ((and true) false)
=> ((λx.λy.((x y) false) true) false)
=> ((true false) false)
=> ((first false) false)
=> false
```
---

`false and true == false`

```
   ((and false) true)
=> ((λx.λy.((x y) false) false) true)
=> ((false true) false)
=> ((second true) false)
=> false
```
---

`false and false == false`

```
   ((and false) false)
=> ((λx.λy.((x y) false) false) false)
=> ((false false) false)
=> ((second false) false)
=> false
```