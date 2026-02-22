Date: 2026-02-22
Tags: #llm-principle

Link: https://www.youtube.com/watch?v=XavrebMKH2A

## Principle

[Nyquist Theorem](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem) indicates that to accurately represent any signal, you need to sample it at least twice the frequency of the highest frequency in that signal

## How it's applicable

AI code is generated faster than humans can review it - reviewing code is the slowest aspect of AI-assisted development

Using only code-review to evaluate generated code would be considered under-sampling according to the theorem

Continuous integration aids in dealing with increased throughput, and is fundamental to quality delivery:

1. determine if a change is releasable
   - requires fast and effective validation
2. automated checks for correctness
   - type-checking
   - linting rules
   - coding standards
   - architecture sanity checks - are patterns being followed?
   - contract tests
3. automated evaluation of behaviour, not only syntax (acceptance testing)

To manage this:

- work in small increments
  - avoid large batches
  - collect feedback
  - evaluate after every change
- optimise for fast feedback
  - ideally faster than the rate of change
  - must be both fast and accurate
  - AI generating invalid code must be detected quickly
- use tests as the source of truth
  - tests verify correctness over-and-above manual review
  - write tests that matter
  - write tests that catch real problems
- use trunk-based development with short-lived branches
- invest in deployment pipeline
  - must be fast, reliable, and repeatable

Code can now be generated faster than humans can review it

Feedback is the number one concern

If you increase production frequency, you must increase feedback frequency
