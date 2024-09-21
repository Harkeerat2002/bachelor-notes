## Table of Contents

---

Table of Contents

Operating System:

Components of a Computer System

Computer System Organization:

Computer System Operations

Common functions of Interrupts

Interrupt Handling

Storage-Device Hierarchy

Storage Structure

Direct Memory Access

Caching

Computer System Archtecture

Single Processor Systems:

Multiprocessors Systems:

Clustered Systems

Operating System Structure

Multiprogramming:

Multitasking (Time-sharing)

Definitions of Operating System Components:

Operating System Services:

Operating System Operations

Dual-mode Operation

Resource Management

Process Management

Memory Management

File-system Management

Mass-Storage Management

I/O System Management

---

## **Operating System:**

- **Operating System** is a program that manages the computer hardware.
- It also provides a basis for Application Programs and acts as an intermediary between computer Users and Computer Hardware.

_An intermediary program between a user of a computer and the computer hardware_**_._**

**Goals:**

- Execute user programs.
- Make the computer system convenient to use.
- Use the computer hardware efficiently.

**Definition:**

- OS is a _resource allocator_
    - Manages all resources
    - Decides between conflicting requests for efficient and fir resource use
- OS is a _control program_
    - Controls execution of programs to prevent errors and improper use of the computer

## Components of a Computer System

![[../../../../Attachments/Untitled 42.png|Untitled 42.png]]

- Hardware
    - Provides basic computing resources
    - CPU, memory, I/O devices
- Operating System
    - Controls and coordinates the use of the hardware among various applications and users
- Application programs
    - Define the ways in which the system resources are used to solve the computing problems of the users.
    - Word processors, compilers, web browsers, database systems, video games
- Users
    - People, machines, other computers

## Computer System Organization:

- One or more CPU’s, device controllers connected through common bus providing access to shared memory
- Concurrent execution of CPU’s and devices competing for memory cycles.

![[../../../../Attachments/Untitled 1 14.png|Untitled 1 14.png]]

- Each **device controller** is in charge of a particular device type and maintains:
    - _Local Buffer Storage_
    - _Set of special purpose registers_
- Operating systems have a **device driver** for each device controller.
- The **device driver** presents an interface to the device to the rest of the OS.

## Computer System Operations

- I/O devices and the CPU can execute concurrently
- Each device controller is in charge of a particular device type.
- Each device controller has a **local buffer**
- CPU moves data from/to main memory to/from local buffers
- I/O is from the device to the local buffer of the controller
- The device controller informs the CPU that it has finished its operation by causing an **interrupt.**

### Common functions of Interrupts

- Interrupt transfers control to the interrupt service routine, generally through the interrupt vector, which contains the address of all the service routines.
- Incoming interrupts are disabled while another interrupt is being processed as a lost interrupt.
- A **trap** is a software-generated interrupt caused either by an error or a user request.
- Operating System is **Interrupt Driven**.

### Interrupt Handling

- The operating system preserves the state of the CPU by storing registers and the program counter.
- **Interrupt vector:** holds the addresses of the interrupt service routines
- Separate segments of code determine what action should be taken for each type of interrupt.
- **Interrupt Steps:**
    - CPU must stop what is doing to handle the interrupt
        - transfer execution to a fixed location
        - fixed location contains starting address where the service routine of interrupt is located
    - Interrupt Service Routine executes
    - On completion, the CPU resumes the interrupted computation.

![[../../../../Attachments/Untitled 2 10.png|Untitled 2 10.png]]

Interrupt Timeline for a single program doing output

## Storage-Device Hierarchy

![[../../../../Attachments/Untitled 3 8.png|Untitled 3 8.png]]

Storage-Device Hierarchy

- The top ones are the fastest, but has less storage and more expensive.
- As the list goes down, the storage increases, and the price decreases, but the price increases.

## Storage Structure

- The CPU can load instructions only from memory, so any programs must first be loaded into memory to run.
- General-purpose computer run most of their programs from re-writable memory, called main memory (also called random-access memory, or RAM).
- Computers also use other forms of memory as well.
- All forms of memory provide an array of bytes. Each byte has its own address.
    - Interaction is achieved through a sequence of _load_ or _store_ instructions to specify the memory addresses.
- Ideally, what is wanted is for the programs and data to reside in the main memory permanently. This arrangement usually is not possible on most systems for two reasons:
    - Main memory is usually too small to store all needed programs and data permanently.
    - Main memory, as mentioned, is volatile - it loses its contents when power is turned off or other lost.
- Hence, most computer systems provide **secondary storage** as an extension of main memory. The main requirement for secondary storage is that it be able to hold large quantities of data permanently.

![[../../../../Attachments/Untitled 4 7.png|Untitled 4 7.png]]

- **Main memory** - only large storage media that the CPU can access directly
- **Secondary storage** - extension of main memory that provides large nonvolatile storage capacity
- Storage systems are organized in hierarchy
    - Speed
    - Cost
    - Volatility
- There is a hierarchy of storage (from CA), which differs from its performance. The faster the storage, the less storage it would have.

## **Direct Memory Access**

- A large portion of operating system code is dedicated to managing I/O, both because of its importance to the reliability and performance of a system and because of the varying nature of the device.
- The form of interrupt-driven I/O is fine for moving small amounts of data but can produce high overhead when used for bulk data movement.
- To solve this problem, **direct memory access (DMA)** is used.

**What it does?**

- Used for high-speed I/O devices able to transmit information at close to memory speeds.
- Device controller transfers blocks of data from buffer storage directly to main memory without CPU intervention.
- Only **one** interrupt is generated per block, rather than one interrupt per byte.

## Caching

- Performed at many levels in a computer (in hardware, operating system, software)
- _Information in use copied from slower to faster storage temporarily._
- Faster storage (cache) checked first to determine if information is there
    - Yes, information used directly from the cache (fast)
    - No, data copied to cache and used there.
- Cache smaller that storage being cached
    - Cache management important design problem
    - Cache size and replacement policy

## Computer System Archtecture

- Types of Computer Systems based on a number of General Purpose Processors:
    - Single Processor Systems
    - Multiprocessor Systems
    - Clustered Systems

### Single Processor Systems:

- One main CPU is capable of executing a general purpose instruction set including instructions from user processes.
- Other special purpose processors are also present which perform device-specific tasks.

### Multiprocessors Systems:

- Also known as **parallel systems** or **tightly coupled systems**
- Has two or more processors in close communication, sharing the computer bus and sometimes the clock, memory, and peripheral devices.
- **Advantages:**
    - Increased throughput
    - Economy of scale
    - Increased Reliability
- **Types of Multiprocessors Systems:**
    - Symmetric Multiprocessing:
        - All the CPUs are the same or similar to each other
    - Asymmetric Multiprocessing:
        - There are master and slave CPUs

### Clustered Systems

- Like multiprocessor systems, clustered systems gather together multiple CPUs to accomplish computational work.
- They are composed of two or more individual systems coupled together.
- Provide high availability
- **Types of Clustered Systems:**
    - Asymmetric Clustered Systems:
        - One machine in Hot-Sandby mode
        - Others run application
    - Symmetric Clustered Systems:
        - Two or more hosts run applications
        - Monitors each other
        - Better

## Operating System Structure

- A computer system can be organized in a number of different ways, which can categorize roughly according to the number of general-purpose processors used.

### Multiprogramming:

- _Multiprogrammed Systems provide an environment in which the various system resources are utilized effectively, but they do not provide for user interaction with the Computer System._
- These system have two (or more) processors, each with a single-core CPU.
- Used for efficiency
- A single user is not allowed to keep CPU and I/O devices busy all the time
- Increases the CPU utilization by organizing the jobs so that the CPU always has one to execute
- A subset of total jobs in the system is kept in **memory** while others are in the **job pool**.
- A job is selected and run through **job scheduling**
- When it is waiting (for I/O devices), OS switches to another job.
    - The code should be written in such a way that the code could be interrupted at any point.

![[../../../../Attachments/Untitled 5 7.png|Untitled 5 7.png]]

**How does it work?**

- The operating system keeps several processes in memory simultaneously.
- The operating system picks and begins to **execute** one of the processes.
- Eventually, the process may have to **wait** for some task, such as an I/O operation to complete.
- In a multiprogramming system, the operating system simply switches to another process, and so on
- Eventually, the first process **finishes** waiting and gets the CPU back.
- As long as at least one process needs to execute, the CPU is **never** **idle**.

### Multitasking (Time-sharing)

- Logical extension in which CPU switches jobs, so frequently that users can interact with each job while it is running, creating **interactive** computing.
- **Response time** should be < 1 second.
- Each user has at least one program in memory→ process
- If several jobs are ready to run at the same time→ CPU Scheduling.
- If processes don’t fit in memory, **swapping** moves them in and out to run.
- **Virtual Memory** allows the execution of processes not completely in memory.

### Definitions of Operating System Components:

- **CPU**: The hardware that executes instructions
- **Processor**: A physical chip that contains one or more CPUs
- **Core**: The basic computation unit of the CPU
- **Multicore:** Including multiple computing cores on the same CPU .
- **Multiprocessor**: Including multiple processors.

## Operating System Services:

- **User Interface**
    - Command Line Interface (CLI)
    - Graphical User Interface (GUI)
- **Program Execution**
- **I/O Operations**
- **File System Manipulation**
- **Communications**
- **Error Detection**
- **Resource Allocation**
- **Accounting**
- **Protecting and Security**

## Operating System Operations

- Since the operating system and its users share the hardware and software resources of the computer system, a properly designed operating must ensure that an incorrect (or malicious) program cannot cause other programs - or the operating system itself - to execute incorrectly.
- In order to ensure the proper execution of the system, it must be able to distinguish between the execution of _operating-system code_ and _user-defined code_.
- **System Calls** provide an interface to the services made available by an Operating System.

### Dual-mode Operation

- **Dual-mode** operation allows OS to protect itself and other system components
    - **User mode** and **kernel mode**
    - **Mode bit** added to the hardware of the computer to indicate the current mode:
        - kernel(0)
        - user(1)
    - Provides the ability to distinguish when the system is running user code or kernel code
    - Some instructions designated as **privileged,** only executable in kernel mode
    - **System call** changes the mode to the kernel, return from call rests it to the user.

![[../../../../Attachments/Untitled 6 7.png|Untitled 6 7.png]]

Transition from User to Kernel Mode

- **Types of System Calls:**
    - Process Control
    - File Manipulation
    - Device Management
    - Information Maintenance
    - Communication

## Resource Management

- The operating system is a **resource manager.**

### Process Management

- A process is a program in execution. It is a unit of work within the system. Program is a **passive entity,** process is an **active entity.**
- The process needs resources to accomplish its task
    - CPU, Memory, I/O, files
    - Initialization data
- Process termination requires the reclaim of any reusable resources.
- **Single-threaded process**
    - One **program counter** specifies the locations of the next instruction to execute.
    - The **process** executes instructions sequentially, one at a time, until completion
- **Multithreaded process**
    - One program counter per thread
- Typically system has many processes, some users, and some operating systems running concurrently on one or more CPUs.
    - Concurrency by multiplexing the CPUs among the processes/threads.
- **Process Management Activities**:
    - **Creating** and **deleting** both user and system processes.
    - **Suspending** and **resuming** processes
    - Providing mechanisms for process **synchronization**
    - Providing mechanisms for process **communication**
    - Providing mechanisms for **deadlock** **handling**

### Memory Management

- All data in memory before processing
- All instructions are in the memory to execute.
- **Memory management activities**
    - Keeping track of which parts of memory are currently being used and by whom
    - Deciding which processes and data to move into and out of memory
    - Allocating and deal-locating memory space as needed.

### File-system Management

- OS provides a uniform, logical view of storage
    - **File:** abstracts physical properties to the logical storage unit
    - Each medium is controlled by the device (i.e., disk drive)
    - Varying properties: access speed, capacity, data transfer rate, access method (sequential or random)
- **File-system management**
    - Files are usually organized into directories
    - Access control on most systems to determine who can access what
- **OS activities include**
    - **Creating** and **deleting** files and directories
    - **Mapping** files onto secondary storage
    - **Backup** files onto stable (non-volatile) storage media.

### Mass-Storage Management

- Usually, disks are used to store data that does not fit in the main memory or data that must be kept for a “long” period of time
- The entire speed of computer operation hinges on the disk subsystem and its algorithms
- **OS activities:**
    - Free-space management
    - Storage allocation
    - Disk scheduling
- **Some storage need not be fast**
    - Tertiary storage includes optical storage, magnetic tape
    - Still must be managed
    - Varies between WORM (write-once, read-many-times) and RW (read-write)

### I/O System Management

- One purpose of OS is to hide peculiarities of hardware devices from the user
- **I/O subsystem responsible for**
    - Memory management of I/O includes buffering (storing data temporarily while it is being transferred), caching (storing parts of data in faster storage for performance)
    - General device-driver interface
    - Drivers for specific hardware devices.