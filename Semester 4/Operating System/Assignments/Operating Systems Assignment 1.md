**Harkeerat Singh Sawhney**

  

### **Exercise 1 -**

==What are the three main purposes of an operating system?==

An informal definition for what a Operating System is, that if a program that acts as an intermediary between a user of a computer and the computer hardware is known as a Operating system. The three main purposes of an operating or goals of the operating systems are:

- Execute User Programs and make solving user problems easier.
- Make the computer system convenient to use.
- Use the computer hardware efficiently manner.

### **Exercise 2-**

==How does the distinction between kernel mode and user mode function as a rudimentary form of protection (security) system?==

The main difference between the both the kernel and user mode is that its providing a rudimentary form of protection. This means that hardware devices are only able to be accessed only when the program is executing in the kernel mode. Similarly there are several other situation this logic is applied for other components as well, for instance only certain instructions could be executed only when the CPU is in the kernel mode. Hence, what this means is that all the critical resources which posses security risk are protected, because in order to access them the program must be in the kernel mode.

### **Exercise 3-**

==Give two reasons why caches are useful. What problems do they solve? What problems do they cause? If a cache can be made as large as the device for which it is caching (for instance, a cache as large as a disk), why not make it that large and eliminate the device?==

One of the main reasons why caches are useful is because of how fast there. This means that they are extremely fast storage systems, which can easily hold the copy of the information which is needed to be accessed. Another advantage is that it holds the next instruction, this means that the processor could beforehand prepare the resources needed for that instruction.

Due to their small and limited size, the cache needs to managed very well, since they are in use majority of time. Hence there methods of cache management needs to be applied for them. Also, caches are usually very expensive to obtain.

Caches are although fast, they are not maintainable, as not only their manufacturing costs are extremely high, but also to maintain them is costly as well. There are also much more delicate as compare to other storage devices.

### **Exercise 4-**

==In a multi-programming and time-sharing environment, several users share the system simultaneously. This situation can result in various security problems.==

1. ==What are two such problems?==
    - **Privacy** - One user could read the private data of another user, which could lead to privacy issued.
    - **Integrity -** One user could corrupt the private data of another user, which could lead to lose of data integrity.
2. ==Can we ensure the same degree of security in a time-shared machine as in a dedicated machine? Explain your answer.==
    
    Due to the fact that it is never known if a software doesn’t contain bugs, hence there could always be an issue with time-shared machines and their degree of security, hence **no**.
    

### **Exercise 5-**

==What is the purpose of interrupts? How does an interrupt differ from a trap? Can traps be generated intentionally by a user program? If so, for what purpose?==

The purpose of an interrupt is that it is a hardware-generated change-of-flow within the system. Hence, when the interrupt is called the interrupt handler is called which deals with the cause of the interrupt. In the other hand, trap is a interrupt which is software is generated, hence they differentiate in that manner. Therefore, they can be generated intentionally by a user program, whenever it is needed. As to why it is needed it would be to signal the completion of an I/O to obviate the need for device polling. It can also be used to call operating system routines as well.