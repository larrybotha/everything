---
aliases:
  - simplified notation
---
parent: [[+ The Lambda Calculus]]

- drop the λ symbols
- move bound variable names to the function declaration
- remove parenthesis that isn't beneficial for disambiguation

e.g. 

```
def id = λx.x
def id x = x

def not = λx.((x false) true)
def not x = x false true
# or
def not x =
	if x
	then false
	else true
 
def make_pair = λx.λy.λf.((f x) y)
def make_pair x y f = f x y

def pred = 
	λn.(((iszero n) zero) (n second))
def pred n = 
	(iszero n) zero (n second)
# or
def pred n =
	if iszero n
	then zero
	else n second 
```