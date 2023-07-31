# Process Management
https://en.wikipedia.org/wiki/Process_management_(computing)

## Context Switch

Process of storing the system state for one task, so that task can be paused and another task resumed.

There are three potential triggers for a context switch:

1. Multitasking
2. Interrupt handling
3. User and Kernel mode switching


<https://en.wikipedia.org/wiki/Context_switch>

## System Calls

Programmatic way in which a computer program requests a service from the kernel. System calls provide an essential interface between a process and the operating system.

System calls are generally not invoked directly, but rather via wrapper functions in glibc.

<https://en.wikipedia.org/wiki/System_call>  
{manpage}`syscalls(2)`
