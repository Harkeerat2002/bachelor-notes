# Chapter 1: Introduction

## **Computer System Structure:**

- Computer system can be divided into four components:
    - Hardware- provides basic computing resources
        - CPU, memory, I/O devices
    - Operating System
        - Controls and coordinates use of hardware among various applications and users
    - Application programs- define the ways in which the system resources are used to solve the computing problems of the users
        - Word processors, compilers, web browsers, database systems, video games
    - Users
        - People, machines, other computers

![[Attachments/Untitled 40.png|Untitled 40.png]]

## Operating System:

An **operating system** is software that manages a computer’s hardware. It also provides a basis for application programs and acts as an intermediary between the computer user and the computer hardware.

**Operating System Goals:**

- Execute user programs and make solving user problems easier
- Make the computer system convenient to use
- Use the computer hardware in an efficient manner

**Operating System** is a resource allocator and control program making efficient use of HW and managing execution of user programs.

- “_The One program running at all time on the computer_” is the **kernel,** part of the operating system.
- Everything else is either:
    - A **system program** (ships with operating system, but not part of the kernel), or
    - An **application program,** all programs not associated with the operating system.

### Computer System Organization:

- Computer-System Operation:
    
    - One or more CPUs, device controllers connect through common **bus** providing access to shared memory
    - Concurrent execution of CPUs and devices competing for memory cycles
    
    ![[Attachments/Untitled 1 13.png|Untitled 1 13.png]]
    
    - I/O devices and the CPU
    - Each device controller is in charge of a particular device type