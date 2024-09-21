## Background

- Concurrent access to shared data may result in data inconsistency
- Maintaining data consistency requires mechanisms to ensure the orderly execution of cooperating processes

## Producer-Consumer Problem

- Supposed that we wanted to provide a solution to the consumer-producer problem that fills **all** the buffers.
- We can do so by having an integer **count** that keeps track of the number of full buffers.
- Initially, count is set to 0.
- It is incremented by the producer after it produces a new buffer and is decremented by the consumer after it consumes a buffer.

### Code for Producer:

![[../../../../Attachments/Untitled 46.png|Untitled 46.png]]

### Code for Consumer

![[../../../../Attachments/Untitled 1 18.png|Untitled 1 18.png]]

## Race Condition

- A situation in which where several processes access an manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place, is called a **race condition.**
- To guard against the race condition, it needs to be ensured that only one process at a time can be manipulating the variable count.
- To make such a guarantee, it needs to be required that a processes be synchronized in some way.

## The Critical-Section Problem

### What is the Problem?

- Consider a system consisting of _n_ processes.
- Each process has a segment of code, called a **critical section,** in which the process may be accessing - and updating - data that is shared with at least one another process.
- The important feature of the system is that, when one process is executing in its critical section, no other process is allowed to execute in its critical section.
- The critical-section problem is to design a protocol that the processes can use to synchronize their activity so as to cooperatively share data.

### Solution to Critical-Section Problem

- **Mutual Exclusion:** If process Pi is execution in its critical section, then no other processes can be execution in their critical section
- **Progress:** If no process is execution in its critical section and there exist some processes that wish to enter their critical section, then selection of the processes that will enter the critical section next cannot be postponed indefinitely.
- **Bounded Waiting:** A bound must exist on the number of times that other processes are allowed to enter their critical section after a process has made a request to enter its critical section and before that request is granted
    - Assume that each process executes at a nonzero speed
    - No assumption concerning relative speed of the **N** processes.

## Peterson’s Solution

- Two-process solution
- Assume that the LOAD and STORE instructions are atomic; that is, cannot be interrupted.
- The two process share two variables:
    - int **turn;**
    - Boolean **flag[2]**
- The variable **turn** indicates whose turn it is to enter the critical section
- The **flag** array is used to indicate if a process is ready to enter the critical section. **flag[]i** = true implies that process **Pi** is ready.

![[../../../../Attachments/Untitled 2 14.png|Untitled 2 14.png]]

The structure of process Pi in Peterson’s Solution

## Hardware Support for Synchronization

- Software-based solutions are not guaranteed to work on modern computer architectures.
- There are three hardware instruction that provide support for solving the critical-section problem.
- These primitive operations can be used directly as synchronization tools, or they can be used to form the foundation of more abstract synchronization mechanism.

### Memory Barriers

- How a computer architecture determines what memory guarantees it will provide to an application program is known as its **memory model.**
- In general, a memory model falls into one of two categories:
    - **Strong ordered,** where a memory modification on one processor is immediately visible to all other processors.
    - **Weakly ordered**, where modifications to memory on one processor may not be immediately visible to other processors.
- Memory Models vary by processor type, so kernel developers cannot make any assumptions regarding the visibility of modifications to memory on a shared-memory multiprocessors.
- To address this issue, computer architectures provide instructions that can _force_ any changes in memory to be propagated to all other processors, thereby ensuring that memory modifications are visible to threads running on other processors.
- Such instructions are known as **memory barriers** or **memory fences.**

![[../../../../Attachments/Untitled 3 12.png|Untitled 3 12.png]]

### Hardware Instructions

- Many modern computer systems provide special hardware instructions that allow us either to test and modify the content of a word or swap the contents of two words **atomically** - that is, as one uninterruptible unit.

![[../../../../Attachments/Untitled 4 11.png|Untitled 4 11.png]]

**Solution using TestAndSet**

- Shared boolean variable lock, initialized to false

![[../../../../Attachments/Untitled 5 11.png|Untitled 5 11.png]]

**Solution using Swap**

- Shared Boolean variable lock initialized to FALSE; Each process has a local Boolean variable key.

![[../../../../Attachments/Untitled 6 10.png|Untitled 6 10.png]]

## Semaphores

- It is a synchronization tool that does not require busy waiting
- Semaphore S - integer variable
- Two standard operations modify **S: wait()** and **signal()**
    - Originally called **P()** and **V()**
- Less complicated
- Can only be accessed via two indivisible (atomic) operations.

![[../../../../Attachments/Untitled 7 8.png|Untitled 7 8.png]]

![[../../../../Attachments/Untitled 8 7.png|Untitled 8 7.png]]

### Semaphore as General Synchronization Tool

- Counting semaphore - integer value can range over an unrestricted domain
- Binary semaphore - integer value can range only between 0 and 1; can be simpler to implement
    - Also known as mutex locks
- Can implement a counting semaphore **S** as a binary semaphore
- Provides mutual exclusion

![[../../../../Attachments/Untitled 9 6.png|Untitled 9 6.png]]

### Semaphore Implementation

- Must guarantee that no two processes can execute **wait()** and **signal()** on the same semaphore at the same time
- Thus, implementation becomes the critical section problem where the wait and signal code are placed in the critical section
    - Could now have busy waiting in critical section implementation
        - But implementation code is short
        - Little busy waiting if critical section rarely occupied
- Note that applications may spend lots of time in critical sections and therefore this is not a good solution

![[../../../../Attachments/Untitled 10 6.png|Untitled 10 6.png]]

![[../../../../Attachments/Untitled 11 6.png|Untitled 11 6.png]]

## Deadlock and Starvation

- **Deadlock** - two or more processes are waiting indefinitely for an event that can be caused by only one of the waiting processes
- **Starvation** - indefinite blocking. A process may never be removed from the semaphore queue in which it is suspended.

## Classical Synchronization Problems

### Bounded-Buffer Problem

- N buffers, each can hold one item
- Semaphore **mutex** initialized to the value 1
- Semaphore **full** initialized to the value 0
- Semaphore **empty** initialized to the value N

![[../../../../Attachments/Untitled 12 5.png|Untitled 12 5.png]]

![[../../../../Attachments/Untitled 13 5.png|Untitled 13 5.png]]

### Readers and Writers Problem

- A data set is shared among a number of concurrent processes
    - Readers - only read the data set; they do **not** perform any updates
    - Writers - can both read and write
- Problem - allow multiple readers to read at the same time. Only one single writer can access the shared data at the same time.
- Shared Data
    - Data set
    - Semaphore **mutex** initialized to 1
    - Semaphore **wrt** initialized to 1
    - Integer **readcount** initialized to 0

![[../../../../Attachments/Untitled 14 5.png|Untitled 14 5.png]]

![[../../../../Attachments/Untitled 15 5.png|Untitled 15 5.png]]

### Dining-Philosophers Problem

![[../../../../Attachments/Untitled 16 5.png|Untitled 16 5.png]]

## Monitors

- A high-level abstraction that provides a convenient and effective mechanism for process synchronization
- Only one process may be active within the monitor at a time