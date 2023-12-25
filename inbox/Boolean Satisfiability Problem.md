Also known as a SAT

> In computer science, the Boolean Satisfiability Problem … is the problem of determining if there exists an interpretation that satisfies a given Boolean formula. In other words, it asks whether the variables of a given Boolean formula can be consistently replaced by the values TRUE or FALSE in such a way that the formula evaluates to TRUE.

e.g. given

```
if ((x and y) and (x and not y)) 
  or ((x or y) and (x or not y)) 
then
  //...
```
which values of `x` and `y` will return `true`?

A flow chart that has a path that terminates in `true` is a SAT
## links and resources

- https://en.wikipedia.org/wiki/Boolean_satisfiability_problem