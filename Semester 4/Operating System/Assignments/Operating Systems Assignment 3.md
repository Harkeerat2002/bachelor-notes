**Harkeerat Singh Sawhney**

  

### Exercise 1- Concurrent Processing

==Original versions of Apple’s mobile iOS operating system provided no means of concurrent processing. Discuss three major complications that concurrent processing adds to an operating system.==

1. The CPU scheduler must be aware of the different concurrent processes and also must choose an appropriate algorithm which then schedules the concurrent processes.
2. Due to the Mobile devices often having a limited amount of memory, this will then effect the performance. This is due to the fact that if a process manages the memory poorly it will then have an overall negative impact on the other concurrent processes. Hence, the operating system than must manage the memory to support the multiple concurrent processes.
3. If the processes are concurrent then the may need to communicate with each other. This will then lead to the operating system to develop one or more methods to provide an inter-process communication

### Exercise 2- Fork sys-call

==When a process creates a new process using the fork() operation, which of the following states is shared between the parent process and the child process?==

1. ==Stack==
2. ==Heap==
3. ==Shared memory segments==
    
    The answer is the **shared memory segments** since they are shared between the parent process and the newly forked child process.
    

### Exercise 3- Context-switch

==Describe the actions taken by a kernel to context-switch between processes.==

1. The OS saves the PC and the user stack pointer of the currently executing process, in response to a clock interrupt and then it transfers the control to the kernel clock interrupt handler.
2. Then it saves the rest of the registers, and also the along with that other machine state, such as the state of the floating point registers.
3. The scheduler is invoked so that the next process can be determined to execute it.
4. After that finally the state of the next process from its PCB and then is retrieved by the OS and the restores the registers. Then the restore operation takes the processor back to the state in which the previous was previously interrupted, executing in user code with user-mode privileges.

### Exercise 4- Init Process

==Explain the role of the== _==init==_ ==process on UNIX and Linux systems in regard to process termination.==

Init tends to the be the first process which starts during the booting of the computer. This happens in any UNIX based operating system. Therefore, init is the parent of all the processes, hence when it start during the booting of the computer it creates a processes from the script which is then stored in the file.