A problem is considered NP-complete when:

1. It is a decision problem, meaning that for any input to the problem, the output is either "yes" or "no".
2. When the answer is "yes", this can be demonstrated through the existence of a short (polynomial length) solution.
3. The correctness of each solution can be verified quickly (namely, in polynomial time) and a brute-force search algorithm can find a solution by trying all possible solutions.
4. The problem can be used to simulate every other problem for which we can verify quickly that a solution is correct. In this sense, NP-complete problems are the hardest of the problems to which solutions can be verified quickly. If we could find solutions of some NP-complete problem quickly, we could quickly find the solutions of every other problem to which a given solution can be easily verified.

## related

- [[nondeterministic polynomial time]]
- [[decision problem]]
- [[Karp's 21 NP-complete problems]]
- [[Complexity theory]]
- [[Boolean Satisfiability Problem]]

## links and resources

- https://en.wikipedia.org/wiki/NP-completeness