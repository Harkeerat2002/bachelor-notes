## Table of Contents

---

Table of Contents

Overview

Multithreaded Server Architecture

Benefits

Multicore Programming

Concurrency vs Parallelism

Programming Challenges

Types of Parallelism

Multithreading Models

Threading Issues

The fork() and exec() System Calls

Signal Handling

Thread Cancellation

---

## Overview

- Most modern applications are **multithreaded**
- Threads run **within** applications
- Process creating is heavyweight while thread creating is lightweight
- Can simplify code, increase efficiency
- Kernels are generally multithreaded.

## Multithreaded Server Architecture

![[../../../../Attachments/Untitled 45.png|Untitled 45.png]]

A single-threaded and multi-threaded process

- Applications can also be designed to leverage processing capabilities on multicore systems.
- Such applications can perform several CPU-intensive tasks in parallel across multiple computing cores.
- Many applications can also take advantage of multiple threads, including basic sorting, trees, and graph algorithms.

![[../../../../Attachments/Untitled 1 17.png|Untitled 1 17.png]]

Multi-threaded server architecture

### Benefits

The benefits of multi-threaded programming can be broken down into four major categories:

1. **Responsiveness:** May allow continued execution if part of the process is blocked, especially important for user interfaces.
2. **Resource Sharing:** Threads share resources of process, easier than shared memory or message passing.
3. **Economy:** Cheaper than process creating, thread switching lower overhead than context switching.
4. **Scalability:** Process can take advantage of multi-processor architectures

## Multicore Programming

- A trend in system design is to place multiple computing cores on a single processing chip where each core appears as a separate CPU to the operating system.
- These systems are referred to as **multicore** and **multithreaded programming** provides a mechanism for more efficient use of these multiple computing cores and improved concurrency**.**

### Concurrency vs Parallelism

- A concurrent system **supports more than one** task by allowing all the tasks to make progress.
- In contrast, a parallel system can perform **more than one task simultaneously**.
- Thus, it is possible to have concurrency without parallelism.

### Programming Challenges

- Multicore or multiprocessor system puts pressure on programmers, challenges include:
    - **Identifying Tasks**
        - This involves examining applications to find areas that can be divided into separate, concurrent tasks.
    - **Balance**
        - While identifying tasks that can run in parallel, programmers must also ensure that the task performs equal work of equal value.
    - **Data Splitting**
        - Just as applications are divided into separate tasks, the data accessed and manipulated by the task must be divided to run on separate cores.
    - **Data Dependency**
        - The data accessed by the tasks must be examined for dependencies between two or more tasks.
        - When one task depends on data from another, programmers must ensure that the execution of the tasks is synchronized to accommodate the data dependency.
    - **Testing and Debugging**
        - When a program is running in parallel on multiple cores, many different execution paths are possible.
        - Testing and debugging such concurrent programs is inherently more difficult that testing and debugging single-threaded applications.

## Types of Parallelism

In general, there are two types of parallelism:

- **Data Parallelism:**
    - Focuses on distributing subsets of the same data across multiple computing cores and performing the same operation on each core.
- **Task Parallelism:**
    - It involves distributing not data but tasks (threads) across multiple computing cores.
    - Each thread is performing a unique operation.

## Multithreading Models

- Support for threads may be provided either at the user level, for **user threads,** or for the **kernel threads** by the kernel**.**
- **User Threads:**
    - Supported **above** the kernel
    - Management done by user-level threads library
- **Kernel Threads**
    - Supported **by** the Kernel
    - Examples - virtually all general-purpose operating systems.

![[../../../../Attachments/Untitled 2 13.png|Untitled 2 13.png]]

User and Kernel threads

- A **relationship** must exist between user threads and kernel threads and kernel threads.
- **Three** Common ways of establishing such as relationship:
    - **Many-To-One Model**
        
        - Many user-level threads mapped to a single kernel thread
        - Switch between threads fast (resources shared)
        - The kernel sees user threads as one process → cannot take advantage of MP architecture.
        
        ![[../../../../Attachments/Untitled 3 11.png|Untitled 3 11.png]]
        
        Many-To-One Model
        
- **One-To-One**
    
    - Each user-level thread maps to the kernel thread
    - Takes **advantage** of MP architecture
    - Context Switch **Slow**
    
    ![[../../../../Attachments/Untitled 4 10.png|Untitled 4 10.png]]
    
    One-To-One Model
    
- **Many-To-Many**
    
    - Allows many user-level threads to be mapped to many kernel threads
    - Takes **advantage** of MP architecture
    - Context switch **faster** than one-to-one
    
    ![[../../../../Attachments/Untitled 5 10.png|Untitled 5 10.png]]
    
    Many-to-Many Model
    

## Threading Issues

### The `fork()` and `exec()` System Calls

- If one thread in one program calls `fork()`, does the new process duplicate all threads, or is the new process single-threaded?
- Some UNIX systems have chosen to have two versions of `fork()` one that duplicates all threads and another that duplicates only the thread that invoked the `fork()` system call.

### Signal Handling

- A **signal** is used in UNIX system to notify a process that a particular event has occurred.
- All signals, whether synchronous or asynchronous, follow the same pattern:
    - A signal is generated by the occurrence of a particular event.
    - The signal is delivered to a process.
    - Once delivered, the signal must be handled.

### Thread Cancellation

- **Thread Cancellation** involves terminating a thread before it has been completed.
- For example, if multiple are concurrently searching through a database and one thread returns the result, the remaining threads might be canceled.
- A thread that is to be canceled is often referred to as the **target thread.** The cancellation of a target thread may occur in two different scenarios:
    - **Asynchronous Cancellation:** One thread immediately terminates the target thread
    - **Deferred Cancellation:** The targeted thread periodically checks whether it should terminate, allowing it an opportunity to terminate itself in an orderly fashion.