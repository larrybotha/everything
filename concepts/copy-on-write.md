A way for efficiently managing memory and processes by creating independent copies of shared memory on-demand, ensuring that changes made by one process don't affect others

e.g. if you have a malleable clay toy, and you want to make sure that it has the following values:

- everyone who wants to look at it can do so without a new toy being created for each of them
- anyone who attempts to make a change to the toy gets a copy of your toy when they try change it

This can be done by:

- put the toy into a copy-on-write box
- pass the toy safely safely around to others
- when someone tries to make a change, the box generates a new malleable clay toy for them, using yours as the template, and leaving yours intact

## links and resources

- https://en.wikipedia.org/wiki/Copy-on-write