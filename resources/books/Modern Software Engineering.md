David Farley
## what is engineering
### fundamentals of an engineering approach
#### applying stability and throughput

- David references [[Accelerate]], and how stability and throughput can be measured, with the result being correlated with high performing teams
- stability and throughput are in contention with each other, but changes to either one usually result in an overall improvement in performance, e.g.
	- external change approval boards don't improve stability - therefore only slow down input - while internal code reviews do improve stability, reducing input, but also reducing work resolving bugs
	- automated testing generally improves stability, at the cost of throughput - the time taken to write the tests, but may also improve throughput by mitigating manual testing

#### the foundations of a software engineering discipline

- exploration, discovery, and learning
- we should focus on becoming experts at learning, and experts ay managing complexity

#### experts at learning

The core behaviours that make for effective software engineering:

- working iteratively
- getting fast, high-quality feedback
- working incrementally
- being experimental
- being empirical

#### experts at managing complexity

The following are symptoms of teams that have lost control of complexity:

- big ball-of-mud systems
- out-of-control technical debt
- crippling bug counts
- teams that are afraid to make changes to systems they own
- the quality of simple, throwaway systems is unimportant
- the quality of large and complex systems is important, otherwise the complexity becomes overwhelming
- managing complexity in a structured way in any information system has the following common ideas:
	- modularity
	- cohesion
	- separation of concerns
	- information hiding/abstraction
	- coupling

#### summary

Fashion and guesswork are not how complexity is managed. When making decisions, we need to think of 2 things:

- stability
	- does the choice increase the quality of the software?
- throughput
	- does this increase the efficiency that we create software of that quality?

If a choice doesn't make either worse, then we can choose either. If not... why choose something that'll make these things worse?

## optimise for learning

### working iteratively

A procedure in which repetition of a sequence of operations yields results successively closer to a desired result

- iteration allows for learning, reacting, and adapting to what we have learnt
- it allows us to make mistakes and correct them
- the [Agile Manifesto](https://agilemanifesto.org) seeks to encourage an approach of skepticism, where ideas are proven false rather than proven true - i.e. falsifiability
- the primary ideas are 'inspect and adapt'
- agile thinking starts with the assumption that we will inevitably get things wrong:
	- we won't understand what the users want
	- we won't get the design right away
	- we won't know if we have caught all bugs
- this way of thinking sets teams up to focus on mitigating costs of mistakes as an ongoing part of their work

#### practical advantages of working iteratively

- thinking in smaller batches
- considering modularity and separation of concerns seriously
- iterative deployments allow us to quickly get feedback from users and course-correct
- iterative releases increase the speed at which we can learn

