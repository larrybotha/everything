How difficult a given problem is

Includes classifications such as:

- P time
  - problems solvable in polynomial time
  - easy problems
- Exp time
  - problems solvable in exponential time
  - hard problems
- R
  - the set of all solvable problems
- NP
  - [[nondeterministic polynomial time]]
  - Exp problems solvable in P time given a nondeterministic algorithm
- [[NP-Complete]]
  - [[decision problem]]s classifiable in NP
  - most decision problems are NP-complete
- NP-Hard
  - problems that can be reduced to other problems in NP, but are not NP themselves
  - combinatorial problems are usually NP-hard

Solvable problems can be solved in the following frames of time:

- polynomial time
- exponential time
- infinite time

Many problems may be simplified by converting them from optimisation problems to decision problems, i.e. from _which of x, y, z_ is optimal, to _is x optimal? is y optimal..._

## takeaways

> think about complexity in terms of time as you scale the inputs that go into the algorithm that you’re using to solve the problem
> _[[The Impostor Handbook]]_

- problems can be solved deterministically or nondeterministically
  - deterministically: a -> b -> c ...
  - nondeterministically a -> b, c, d, ..., or n -> ...
    - Exp problems can be made into P problems by approaching the problem nondeterministically
- NP is nondeterministic polynomial time
- problems where we are optimising for a combination of things is known as [[combinatorial optimisation]]
  - e.g. optimising happiness for a group of people selecting which pub to go to

### polynomial time

- also known as "P time"
- Problems that scale according to a [[polynomial]] equation
- list operations, like sorting, searching, zipping, and enumeration are all P-time
- simple problems are usually P-time - not something you'd want to do exclusively as a developer

### exp time

- exponentially difficult problems, i.e. something of the form `2^n`
- a weighted graph is exp time

### All Solvable Problems (R)

- problems that can be solved in a finite amount of time

### Infinitely Complex Problems Beyond R

- problems that require an infinite amount of time to solve
  - e.g. [[The Halting Problem]]
- must problems that exist are undecidable

> it’s not possible to write a generalized program that can decide if any other program will halt.
> [[The Impostor Handbook]]

### NP

- nondeterministic polynomial time problems - problems that can be solved in polynomial time, with the use of a nondeterministic algorithm

### Reduction

- can a problem that is not a [[decision problem]] be reduced to a series of decision problems?
  - e.g. which is the best pub, out of a set of pubs, for a group to go to based on each person's preferences
    vs
    does the group want to go to pub X?
    does the group want to go to pub Y?
    ...

### verification

- verification of combinatorial problems requires a lot of effort:
  - does `xa` solve the problem?
  - does `xb` solve the problem?
  - does `ya` solve that problem?
  - ...
- verification of decision decision problems is easier than that of combinatorial problems

## related

- [[The Impostor Handbook]]
