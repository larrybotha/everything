---
tags:
  - resource/article
---
https://archive.is/2025.03.28-171144/https://animeshgaitonde.medium.com/what-i-wish-i-knew-before-system-design-interviews-20376f8deafa

## takeaways

- the purpose of system design interviews is to convey your structured thinking, technical depth and breadth, and reasoning skills to the interviewer
- demonstrate understanding of ownership of the system
	- consider all devices as part of the system - server-side and client-side
		- what are the limitations and constraints of all devices
		- what are the constraints and SLAs of 3rd party services
		- be explicit about assumptions
	- main points:
		- consider all entities, their limitations, and how they affect your design choices
		- ensure that every component is discussed, explaining its functionality
		- discuss long-term implications of certain design choices, trade-offs, and how things may be extended or replaced as needs change
- demonstrate a deep understanding of bottlenecks
	- identification of areas where an application or service will fail to scale is important
	- knowing where edge-cases are, providing solutions, and understanding the trade-offs
	- how to develop this skill: 
		- back-of-the-envelope calculations are important, but require understanding what capacity different services can operate under. e.g. how many requests a server can handle, number of connections a db can handle
		- highlight bottlenecks, and iterate as one works through the problem
		- propose solutions to the bottlenecks, e.g. a db failing under load could be assisted by an async queue, but this introduces complexity into the system
- time management
	- don't spend excessive amounts of time on unimportant areas
	- scope features to 2-3 features max
	- follow up with the interviewer to determine if certain areas need more information
- follow a structured approach
	- see "six step framework" link below
	- start at a high-level, gathering requirements, identify entities and actors, consider API design, then dive deep, consider bottlenecks and trade-offs of design
	- the design should follow a logical approach, with components linking to each other
	- the final design should focus on both functional and non-functional completeness
- avoid memorising answers
	- it's clear when an answer is interrogated and the response is not coming from understanding
	- instead:
		- master the fundamentals; OSes, networking, comms protocols, dbs
		- identify assumptions one holds and challenge them
		- identify and understand patterns in systems, e.g. newsfeeds, such as LinkedIn, Instagram, etc. will follow the same principles


## links and resources

- https://engineeringatscale.substack.com/p/system-design-interview-success-six-step-framework