**Harkeerat Singh Sawhney**

  

### Exercise 1- System Calls

==What is the purpose of system calls?==

System calls provide an interface to the serviced made available by an operating system. Hence, it allows an interface between a process and operating system which allows user-level processes to request services of the operating system.

### Exercise 2- Operating System Services

==List five services provided by an operating system, and explain how each creates convenience for users. In which cases would it be impossible for user-level programs to provide these services? Explain your answer.==

The **five services** which is provided by an operating system are as follows:

1. **_Program Execution:_**
    
    In this the operating system loads the contents of a file into the memory and then it begins the execution. This is because a user-level program is not able to be trusted to allocate the CPU time.
    
2. **_I/0 Operations:_**
    
    The communication with the disks, tapes, and other devices is a necessity at a low level. This is because the user is only needed to specify the device the operation is performed on, and then later on the system converts that request into device-or controller-specific commands. Also the User-level programs cannot be trusted to access only the devices they should have access to and to access them only when they are otherwise unused.
    
3. **_File-system Manipulation:_**
    
    In the file create, there are many details in file creation, deletion, allocation, and naming that the users should not use. Also blocks, of disks space are used by files and must be tracked. Deleting the file also requires removing the name files information and also also freeing the allocated blocks.
    
4. _**Communications:**_
    
    In order to pass messages between the systems, it also requires them to be turned into packets of information, and then they would be send over to the network controller, which is then transmitted across the communications medium, and reassembled by the destination system.
    
5. _**Error Detection:**_
    
    Error detection could occur at both the hardware and also in the software levels. At the hardware level, all of the data transfers must also be inspected to ensure that the data has not be corrupted during its transfer. Along with that that all the data on media also must be check to be sure that they have not changed since they were written to the media. At the software level, media must also check for the data consistency.
    

### Exercise 3- System Call Parameters

==Describe three general methods for passing parameters to the operating system.==

1. Passing the parameters in the Registers
2. The program could push, or place the parameters onto the stack, and then later pop it off the stack by the operating system.
3. Registers can pass the starting addresses of blocks of parameters.

### Exercise 4- Inter-process Communication

==What are the two models of inter-process communication? What are the strengths and weaknesses of the two approaches?==

There are two models for the inter-process communication, which are:

- Message-passing Model
- Shared-memory Model

Message passing has an advantage for exchanging smaller amounts of data, because then no conflicts would be need to be avoided. It is also much easier to implement than for instance shared memory for inter-computer communication. Shared memory also allows there to be a maximum speed and convenience of communication, since it can be done at memory transfer speeds when it takes place within a computer. However, at the other hand it also compromises on protection and synchronization between the processes sharing memory.

### Exercise 5- Micro-kernel

==What is the main advantage of the micro-kernel approach to system design? How do user programs and system services interact in a micro-kernel architecture? What are the disadvantages of using the micro-kernel approach?==

_**Advantages:**_

- Adding a new service does not requires modifying the kernel.
- It is also much more secure as more operations are done in the user mode as compare to kernel mode.
- The kernel is also much more simpler in design and also in functionality which results in a much more reliable operating system.

The way in which user programs and the system services interact with each other in a micro-kernel architecture is through inter-process communication mechanisms such as messaging. These messages would then conveyed by the operating system.

_**Disadvantages:**_

- The overheads are the biggest disadvantages since they are associated with the inter-process communication and the frequent use of the operating system’s messaging functions in order to enable the user process and the system service to interact with each other.