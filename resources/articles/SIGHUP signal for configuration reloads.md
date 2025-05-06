---
tags:
  - resource/article
---
Link: https://blog.devtrovert.com/p/sighup-signal-for-configuration-reloads

## takeaways

- SIGHUP is "signal hangup"
- terminals accept input, sending it to a shell
- a shell executes the input, sending the output to the terminal to render
- a terminal ams shell communicate via PTY - a pseudo-terminal
	- terminal requests a virtual device from the OS by opening `/dev/ptmx`
	- kernel creates a master fd for the terminal to write input to and read output from, and a slave fd (e.g. `/dev/pts/2`) used by the shell to read keystrokes and write output to
- a new terminal window forks a child process which makes a call to `setsid()` which creates a new session, and makes it the session leader
- a session is what holds all the jobs related to that terminal instance
	- the commands in the session need your input and must be output - this is managed by the slave fd of the PTY. The slave is called the _controlling terminal_
- closing a terminal results in a sequence of events, completing with the controlling terminal sending SIGHUP to the child processes it spawned
- daemons are background processes designed to run independently of terminals. They do not receive ctrl-C or ctrl-Z inputs. SIGHUP is not meaningful to daemons like it is shell processes, because a closing shell will have no impact on the daemon
- SIGHUP thus became a standard to tell daemons to reload their configs