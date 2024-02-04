---
tags:
  - resource/article
---
Link: https://opensource.com/article/19/10/strace

- users interface with command line applications, system calls interface with the kernel 

```
Command-line utility 
  -> Invokes functions from system libraries (glibc) 
  -> Invokes system calls
```

- `strace` is for tracing system calls
- `ltrace` is for tracing library calls
- operating system can roughly be divided into two modes:
	- Kernel mode: A privileged and powerful mode used by the operating system kernel
	- User mode: Where most user applications run
- 

## links and resources

- [[strace]]
- [[ltrace]]