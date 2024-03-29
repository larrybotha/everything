Link: https://youtu.be/RqubKSF3wig?si=zNjWkbJvuU-ma55q

- ex-Googler
- builds applications as a sole developer
- evaluated every tool he uses and determined all he needed was Go and SQLite
	- only so much that someone can hold in their head
	- uses Go client and server-side
- use 1 computer until you have to scale
	- most cloud computing is unnecessary using this approach
	- a single computer can handle far more load than most services are expected to handle
		- this is true for many services even at a company the size of Google
- SQLite has WAL, a write-ahead feature that is useful for making writes at the same time as there are many reads