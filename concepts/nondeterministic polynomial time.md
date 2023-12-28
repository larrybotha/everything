A complexity class in [[Complexity theory]] used to classify [[decision problem]]s

NP is the set of decision problems that can be solved in polynomial time by the following equivalences:

- a nondeterministic Turing machine
	- i.e. a nondeterministically generated guess about the solution
- or for which the problem instances, where the answer is "yes," have proofs verifiable in polynomial time by a deterministic Turing machine
	- i.e. a deterministic algorithm that verifies the guess is correct

A problem is considered NP if the following all hold:

- Solvable in exponential time (Exp)
- Verifiable in polynomial time (P)
- Also solvable in polynomial time by nondeterministic methods

Many problems that we would like to solve efficiently with a computer, but cannot, are NP

Any problem in NP can be reduced to a [[Boolean Satisfiability Problem]]. 

## links and resources

- https://en.wikipedia.org/wiki/NP-completeness