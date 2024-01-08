---
tags:
  - resource/article
---

Link: https://stackoverflow.blog/2023/12/27/stop-saying-technical-debt

- calling "bad code" _technical debt_ can be problematic, as there may be legal,
  business, or other non-technical reasons why the code is written the way it
  a. Business needs change, legal reasons may not be opaque
- allowing developers to fix "technical debt" willy-nilly often leads to them
  addressing bugbears, instead of addressing debt that actually affects the
  business
- _technical debt_ should ideally be described as work that affects the
  maintenance load of writing new features - which aspects are taking time
  from improving and releasing new features?
- the goal of diminishing technical debt should be to achieve a _negative
  maintenance load - code should become \_more maintainable_ over time
  - regular allocation of time for updating dependencies
  - encouraging documentation of libraries, dependencies, and interactions
    between modules and libraries to mitigate _context loss_ when team members
    leave
    - _context loss events_ - when team members with critical and undocumented
      knowledge leave, and the team discovers at that point that they now have
      no idea how maintainable the associated codebase is
  - prioritising rearchitecting of the codebase when the team is constantly
    working around architectural choices
    - resilient designs are more flexible, accounting for possible future
      considerations

## related

- [[Technical Debt - An Analytical Approach]]
