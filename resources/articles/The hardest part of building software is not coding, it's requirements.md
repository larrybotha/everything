---
tags:
  - resource/article
---

Link: https://stackoverflow.blog/2023/12/29/the-hardest-part-of-building-software-is-not-coding-its-requirements

- AI is a concern for developers, as they feel their jobs may be taken, but
  writing code is easier than implementing and maintaining requirements
- chess is deterministic, and can be described by a rules engine. Thus has a
  relatively low complexity to automate using AI:
  - it has a finite number of pieces and spaces
  - it has a clearly-defined objective
  - it has clearly-defined rules
  - in each turn, there are a finite number of moves
- driving cars is largely a rules-based engine, but is also non-deterministic,
  and thus is much more difficult to automate without relying on human interaction:
  - the rules of the road are well-defined
  - the number of variables are not finite
  - the number and type of obstacles a vehicle may encounter on a given journey
    are unpredictable, the further you get into the long-tail of probable
    situations
- SLAs (service-level agreements) increase in difficulty exponentially for each
  9 added to the SLA:
  - 99% allows for 5256m/yr (87.6hrs/yr, or +-3 days) downtime
  - 99.9% allows for 526.5m/yr (8.76hrs/yr) downtime
  - 99.99% allows for 52.6m/yr downtime
  - 99.999% allows for 5.2m/yr downtime
  - 99.9999% allows for .52m/yr downtime
- chess has an end-goal, whereas software is constantly changing as business
  needs change
