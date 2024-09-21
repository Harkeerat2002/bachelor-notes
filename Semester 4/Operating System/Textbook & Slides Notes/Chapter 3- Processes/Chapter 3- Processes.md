## Table of Contents

---

Table of Contents

Process Concept

What is inside a Process?

Process State

Process Control Block

Process Scheduling

Scheduling Queues

CPU Scheduling

Context Switch

Schedulers & Swapping

Process Creation

Process Termination

Interprocess Communication

Shared Memory Systems

Message Passing Systems

---

## Process Concept

- An operating system executes a variety of programs:
    - Batch system jobs
    - Time-shared systems - user programs or tasks
- What to call all the CPU activities?
    - Early computers were batch systems that executed **jobs,** followed by the emergence of time-shared systems that ran **user programs,** or **tasks.**
- **Process:**
    - A **program in execution**; process execution must progress in a sequential fashion.
- **Thread:**
    - A thread is the **unit of execution within a process.** A process can have anywhere from just one thread to many threads.

### What is inside a Process?

- **Program Counter**
    - The status of the current activity of a process is represented by the values of the program counter.
- **Text Section**
    - The executable code
- **Data Sections**
    - Global variables
- **Heap Section**
    - Memory that is dynamically allocated during program run time
- **Stack Section**
    - Temporary data storage when invoking functions (such as function parameters, return addresses, and local variables)

  

![[../../../../Attachments/Untitled 44.png|Untitled 44.png]]

Layout of process in memory

- The size of the **text** and **data** **sections** are **fixed**, as their sizes do not change during program run time.
- However, the **stack** and **heap** sections can **shrink and grow dynamically** during program execution.
- Each time a function is called, an **activation record** containing function parameters, local variables, and the return address is pushed onto the stack.

## Process State

![[../../../../Attachments/Untitled 1 16.png|Untitled 1 16.png]]

Diagram of process state

- As a process executes, it **changes states**.
- The state of a process is defined in part by the current activity of that process.
- It changes the state as follows:
    - **new:** The process is being created
    - **running:** Instructions are being executed
    - **waiting:** the process is waiting for some event to occur
    - **ready:** The process is waiting to be assigned to a processor
    - **terminated:** The process has finished execution

## Process Control Block

![[../../../../Attachments/Untitled 2 12.png|Untitled 2 12.png]]

Process control block (PCB)

- Each process is represented in the operating system by a **process control block (PCB) -** also called a **task control block.**
- Use to **represent** a process in the Operating System.
- It contains many pieces of information associated with a specific process, including these:
    - **Process State:** The state may be new, ready, running, waiting, halted, and so on.
    - **Process Number:** A unique number or an id of the process
    - **Program Counter:** The counter indicates the address of the next instruction to be executed for this process.
    - **CPU Registers:** Along with the program counter, this state information must be saved when an interrupt occurs, to allow the process to be continued correctly afterward when it is rescheduled to run. Registers that are being used by the process.
    - **CPU-scheduling information:** This information may include items such as the value of the base and limit registers and the page tables, or the segment tables, depending on the memory system used by the operating system.
    - **Memory Management Information:** Represents the memory that is being used by the process.
    - **Accounting Information:** This information includes the amount of CPU and real-time used, time limits, account numbers, job or process numbers, and so on. Keeps account of all the resources being used by the process.
    - **I/O status information:** This information includes the list of I/O devices allocated to the process, a list of open files, and so on.

## Process Scheduling

- The objective of multi-programming is to have some process **running at all times** so as to maximize CPU utilization.
- The object of time sharing is to switch a CPU core among processes so frequently that users, can **interact with each program** while it is running.
- To meet these objectives, the **process scheduler** selects an available process for program execution on the CPU.
    - Each CPU core can run **one** process at a time.
    - If there are more processes, the rest will have to wait until the CPU is free and can be rescheduled.
- The number of processes currently in memory is known as the **degree of multiprogramming.**

## Scheduling Queues

- There are two types of scheduling Queues; **Ready Queue** and **Job Queue.**
- **Ready Queue:**
    - As processes enter the system, they are put into a **ready queue,** where they are ready and waiting to execute on a CPU’s core.
- **Job Queue:**
    - Set of all processes in the system.
    - As processes enter the system, they are put into a job queue, which consists of all processes in the system.
- Processes that are waiting for a certain event to occur - such as completion of I/O are placed in a **wait queue.**
- Process migrate among the various queues.

## CPU Scheduling

- The role of the **CPU scheduler** is to select from among the processes that are in the ready queue and allocate a CPU frequently.
- Some operating systems have an intermediate form of scheduling, known as **swapping,** whose key is that sometimes it can be advantageous to remove a process from memory and thus reduce the degree of multi-programming.

## Context Switch

![[../../../../Attachments/Untitled 3 10.png|Untitled 3 10.png]]

Diagram showing context switch from process to process

- Interrupts cause the operating system to change a CPU core from its current task and to run a kernel routine.
- When an interrupt occurs, the system needs to save the current **context** of the process running on the CPU core so that it can restore that context when its processing is done, essentially suspending the process and then resuming it.
- Context means the **current state** or the **current information** about the process.
- The context is represented in the **PCB (Process Control Block)** of the process.
- Generically, a **state save** is performed of the current state of the CPU core, be it in kernel or user mode, and then the **state restores** to resume operations.
- Switching the CPU core to another process requires performing a state save of the current process and a state restore of a different process.
- This task is known as a C**ontext Switch.**
- Context Switch time is **pure overhead** because the system does no useful work while switching.

## Schedulers & Swapping

![[../../../../Attachments/Untitled 4 9.png|Untitled 4 9.png]]

- **Long-term Scheduler** (or job scheduler)- Selects which processes should be brought into the _ready queue_.
    - Long-term Scheduler is invoked very infrequently (seconds, minutes) → (may be slow).
    - The long-term scheduler **controls the degree of multi-programming.**
- **Short-term Scheduler** (or CPU scheduler) - selects which process (from the r_eady queue_) should be executed next and allocates CPU.
    - Short-term Scheduler is invoked very frequently (milliseconds) → (must be fast)
- A process can be described as either:
    - **I/O-bound process -** spends more time doing I/O than computations, many short CPU bursts
    - **CPU-bound process-** spends more time doing computations; few very long CPU bursts

## Process Creation

![[../../../../Attachments/Untitled 5 9.png|Untitled 5 9.png]]

A tree of processes on a typical Linux system

- A process may create several new processes, via a **create-process system call**, during the course of execution.
- The **creating process** is called a **parent process,** and the **new processes** are called the **children of that process.**
- Each of these new processes may in turn create other processes, forming a tree of processes.
- When a process creates a new process, **two possibilities exist in terms of execution**:
    - The parent continues to execute **concurrently** with their children
    - The parent **waits** until some or all of their children have terminated.
- **Resource sharing:**
    - Parents and children share all resources
    - Children share a subset of parent’s resources
- **Address space**
    - The child process is a **duplicate** of the parent process (it has the same program and data as the parent)
    - Child has a **new program** loaded into it.
- **UNIX examples**
    - **fork** system call creates a new process
    - **exec** system call is used after a **fork** to replace the process memory space with a new program.

![[../../../../Attachments/Untitled 6 9.png|Untitled 6 9.png]]

Example of Fork being used

![[../../../../Attachments/Untitled 7 7.png|Untitled 7 7.png]]

Process creation using `fork()` system call

## Process Termination

- A **process terminates** when it **finished executing its final statement** and asks the operating system to **delete it by using the** `**exit()**` **system call.**
- At that point, the process may **return a status value** (typically an integer) **to its parent process** (via the `wait()` system call.
- **All the resources of the process** including physical and virtual memory, open files, and I/O buffers **are deallocated** by the operating system.
- **Termination can occur in other circumstances as well:**
    - A process can cause the termination of another process via an appropriate system call.
    - Usually, such a system call is invoked only by the parent of the process that is to be terminated.
- **Reasons for the parent process to terminate its child process:**
    - The child has **exceeded** its usage of some of the resources that it has been allocated.
    - The task assigned to the child is no longer required.
    - The parent is exiting, and the operating system does not allow a child to continue if its parent terminates.
- When all children are terminated it's called **cascading termination.**

## Interprocess Communication

- Processes execution concurrently in the operating system may be either **independent processes** or **cooperating processes**.
- **Independent Processes:**
    - They cannot affect or be affected by the other processes executing in the system.
    - A process is **_independent_** if it does not share data with any other processes executing in the system.
- **Cooperating Processes:**
    - They can affect or be affected by the other processes executing in the system.
    - A process is **_cooperating_** if it can affect or be affected by the other processes executing in the system.
- **Reasons to provide an environment that allows process cooperation:**
    - **Information sharing:** Since several applications may be interested in the same piece of information (for instance, copying and pasting), we must provide an environment to allow concurrent access to such information.
    - **Computation Speedup:** If we want a particular task to run faster, we must break it into sub-tasks, each of which will be executed in parallel with the other. Notice that such a speedup can be achieved only if the computer has multiple processing cores.
    - **Modularity:** We may want to construct the system in a modular fashion, dividing the system functions into separate processes or threads.
    - **Convenience:** For the user, since the user can run different processes at the same time.
- Cooperating processes require an **interprocess communication (IPC)** mechanism that will allow them to exchange data - that is, **send data** to and **receive data** from each other.
- **Two fundamental models of interprocess communication:**
    
    ![[../../../../Attachments/Untitled 8 6.png|Untitled 8 6.png]]
    
    Communication Models. (a) Shared Memory. (b) Message Passing
    
    - **Shared Memory**
        - In the shared memory, a region of memory that is shared by cooperating processes is established.
        - Processes can then exchange information by reading and writing data to the shared region
    - **Message Passing**
        - In the message passing model, communication takes place by means of messages exchanged between the cooperating processes.

### Shared Memory Systems

- Interprocess Communication using shared memory requires communication processes to establish a region of shared memory.
- Typically, a shared-memory region **resides in the address space of the process creating the shared memory segment**.
- Other processes that wish to communicate using this shared memory segment must attach it to their address space.
- Normally, the operating system tries to **prevent one process** from accessing another process’s memory
- Share memory requires that two or more processes **agree to remove this restriction**.

### Message Passing Systems

- Message passing provides a mechanism to allow processes to communicate and synchronize their actions without sharing the same address space **and is particularly useful in a distributed environment, where the communicating processes may reside on different computers connected by a network.**
- **Two operations provided by the message-passing facility:**
    - **send (message)**
    - **receive (message)**
- Messages sent by a process can be of either **fixed** or **variable size**
    - **Fixed Size:**
        - The system-level implementation is straightforward.
        - But makes the task of programming more difficult.
    - **Variable Size:**
        - Requires a more complex system-level implementation.
        - But the programming task becomes simpler.
- A **communication link** must exist between two processes if they want to communicate with each other.
- There are **several methods for logically implementing a link** and the `send()`/ `receive()` operations, like:
    - **Direct or indirect communication:**
        - **Direct Communication:** Each process that wants to communicate must explicitly name the recipient or sender of the communication
        - **Indirect Communication:** The messages are sent to and received from mailboxes, or ports.
    - **Synchronous or asynchronous communication:**
        - Message passing may be either **blocking** or **nonblocking-** also known as **synchronous** and **asynchronous.**
        - **Blocking Send:** The sending process is blocked until the message is received by the receiving process or by the mailbox.
        - **Nonblocking Send:** The sending process sends the message and resumes operation.
        - **Blocking Receive:** The receiver blocks until a message is available.
        - **Nonblocking Receive:** The receiver retrieves either a valid message or a null.
    - **Automatic or explicit buffering:**
        - **Buffering:** When communication is direct or indirect, messages exchanged by communicating processes reside in a temporary queue. Basically, such queues can be implemented in three ways:
            - **Zero Capacity:** The queue has a maximum length of zero; thus, the link cannot have any messages waiting in it.
            - **Bounded capacity:** The queue has a finite length of n; thus, at most n messages can reside in it.
            - **Unbounded capacity:** The queue length is potentially infinite; thus any number of messages can wait in it.