- **CPU scheduling is the basis of multiprogrammed operating systems.**
- By switching the CPU among processes, the operating system can make the computer more productive.

## Basic Concepts

- In a **single-processor system**, only one process can run at a time.
- Any others must wait until the CPU is free and can be rescheduled.
- **Multiprogramming:**
    - The objective of multiprogramming is to have some process running at all times, to maximize CPU utilization.
    - Ensures maximum CPU utilization.
    - Several processes are kept in memory at one time.

## CPU-I/O Burst Cycle

![[../../../../Attachments/Untitled 47.png|Untitled 47.png]]

Alternating sequence of CPU and I/O bursts

- Process execution consists of a cycle of **CPU execution** and **I/O wait.**
- Processes alternate be**t**ween these **two states.**
    - **CPU burst** = **CPU exection**
    - **I/O burst = I/O wait**
- The success of CPU scheduling depends on an observed property of processes: process execution consists of a **cycle** of CPU execution and I/O wait.
- Process execution begins with a **CPU burst**.
- That is followed by an **I/O burst**, which is followed by another CPU burst then another I/O burst, and so on.

## CPU Scheduler

- Whenever the CPU becomes idle, the operating system must select one of the processes in the **ready queue to be executed**.
- The selection process is carried out by the **CPU scheduler,** which selects a process from the processes in memory that are ready to execute and allocates the CPU to that process.
- The ready queue is not necessarily a first-in, first-out (FIFO) queue.
- A ready queue can be implemented as a
    - **FIFO queue**
    - **Priority Queue**
    - **Tree**
    - **Unordered Linked List**

## Preemptive and Nonpreemptive Scheduling

![[../../../../Attachments/Untitled 1 19.png|Untitled 1 19.png]]

- CPU scheduling decisions may take place when:
    1. Process **switches** from **running** to **waiting** state.
    2. Process **switches** from **running** to **ready** state
    3. Process **switches** from **waiting** to **ready** state
    4. Process **terminates**
- When scheduling takes place only under **circumstances 1 and 4**, there is no choice in terms of scheduling. A new process (if one exists in the ready queue) must be selected for execution)
- There is a choice in **circumstances 2 and 3**.
- **Non-preemptive Scheduling:**
    - When the scheduling takes place only under **circumstances 1 and 4**, we say that the scheduling scheme is **non-preemptive** or **cooperative.**
    - Under **non-preemptive scheduling**, once the CPU has been **allocated** to a process, the process **keeps** the CPU until it **releases** it either by **terminating** or by **switching** to the **waiting state**.
- **Preemptive Scheduling:**
    - When the scheduling takes place under **circumstances 2 and 3**, it is said to be **preemptive**.
    - Under **preemptive scheduling**, the process is still running but **instead** of giving the CPU to the same process, it can be given to a different process.

## Dispatcher

![[../../../../Attachments/Untitled 2 15.png|Untitled 2 15.png]]

The role of the dispatcher

- Another component involved in the CPU-scheduling function is the **dispatcher.**
- The dispatcher is the module that gives **control** of the CPU’s core to the **process** selected by the CPU scheduler.
- The function involves the following
    - **Switching context** from one process to another
    - **Switching** to **user mode**
    - **Jumping** to the proper location in the user program to resume that program
- The dispatcher should be **fast** as possible since it is invoked during every context switch.
- The time it takes for the dispatcher to stop one process and start another running is known as the **dispatch latency.**

## Scheduling Criteria

- Different CPU-scheduling algorithms have **different properties**, and the choice of a particular algorithm may favor one class of processes over another.
- In choosing which algorithm to use in a particular situation, we must consider the properties of the **various algorithms**.
- **Criteria for CPU Scheduling:**
    - **CPU Utilization:** Keeps the CPU as busy as possible
    - **Throughput:** Number of processes that complete their execution per time unit
    - **Turnaround time:** Amount of time to execute a particular process
    - **Waiting time:** Amount of time a process has been waiting in the ready queue
    - **Response time:** Amount of time from the submission of a request until the first response is produced.

## Scheduling Algorithms

### Optimization Criteria

- Max CPU Utilization
- Max throughput
- Min turnaround time
- Min waiting time
- Min response time

### First-Come, First-Served Scheduling

- With this scheme, the **process that requests the CPU first is allocated the CPU first**.
- The implementation of the FCFS policy is **easily managed with a FIFO queue**.
- When a process enters the ready queue, its **PCB is linked to the tail of the queue**.
- When the CPU is free, it is allocated to the process at the head of the queue.
- The running process is then removed from the queue.
- On the negative side, the **average waiting time under the FCFS policy is often quite long.**

![[../../../../Attachments/Untitled 3 13.png|Untitled 3 13.png]]

- If the processes arrive in the orders **P1, P2, and P3**, and are served in FCFS order, we get the results in the following chart.

![[../../../../Attachments/Untitled 4 12.png|Untitled 4 12.png]]

- The waiting time is 0 milliseconds for process P1, 24 milliseconds for process P2, and 27 milliseconds for process P3. Thus, the average waiting time is (0+24+27) / 3 = 17 milliseconds.
- If the process arrives in the order P2, P3, and P1, however, the results will be as shown in the following Gantt chart

![[../../../../Attachments/Untitled 5 12.png|Untitled 5 12.png]]

- The average waiting time is now (6 + 0 + 3)/3 = 3 milliseconds. This reduction is substantial. Thus, the average waiting time under an FCFS policy is generally not minimal and **may vary substantially** if the processes’ CPU burst times vary greatly.
- **The FCFS scheduling algorithm is non-preemptive**
- **Advantages:**
    - Simple
    - User-Friendly
    - Easy to Implement
    - First come first serve
- **Disadvantages:**
    - Long Waiting Time
    - Lower Device Utilization
    - Favors CPU over I/O
    - Not ideal for Time-Sharing Systems

## Shorted-Job-First scheduling (SJF)

- A different approach to CPU scheduling is the **shortest-job-first (SJF)** scheduling algorithm.
- The algorithm associates with each process the **length of the process’s next CPU burst**.
- When the CPU is available, it is assigned to the process that has the **smallest next CPU burst**.
- If the next CPU burst of two processes is the same, FCFS scheduling is used to break the tie.
- **Two schemes:**
    - **Non-preemptive:** Once the CPU was given to the process it cannot be preemptive until completes its CPU burst
        
        ![[../../../../Attachments/Untitled 6 11.png|Untitled 6 11.png]]
        
    - **Preemptive:** If a new process arrives with CPU burst length less than the remaining time of the currently executing process, preempt. This scheme is known as the Shortest-Remaining-Time-First (SRTF)
        - **Waiting Time = Total Waiting Time - No. of milliseconds Process executed - Arrival Time**

![[../../../../Attachments/Untitled 7 9.png|Untitled 7 9.png]]

  

- **Disadvantages:**
    - **Length of Next CPU Burst**
        - The real difficulty with the SJF algorithm is **knowing the length of the next CPU request**
        - Although the SJF algorithm is optimal, it cannot be implemented at the level of short-term CPU scheduling
        - There is no way to know the length of the next CPU burst.

## Priority Scheduling

- A priority is associated with each process, and the CPU is allocated to the process with the highest priority
- Equal-priority processes are scheduled in FCFS order.
- An SJF algorithm is simply a priority algorithm where the priority is the inverse of the (predict) next CPU burst.
    
    The larger the CPU burst, the lower the priority, and vice versa.
    
- Priority scheduling can be either **preemptive** or **non-preemptive.**
- A **preemptive priority scheduling algorithm** will preempt the CPU if the priority of the newly arrived process is higher than the priority of the currently running process.
- A **non-preemptive priority scheduling algorithm** will simply put the new process at the head of the ready queue.

![[../../../../Attachments/Untitled 8 8.png|Untitled 8 8.png]]

### Problem with Priority Scheduling

- A major problem with priority scheduling algorithms is **indefinite blocking** or **starvation.**
- A process that is ready to run but waiting for the CPU can be considered blocked.

## Round Robin (RR)

- The round-robin (RR) scheduling algorithm is designed especially for time-sharing systems.
- It is similar to FCFS scheduling, but **preemption** is added to switch between processes.
- A small unit of time, called a **time quantum or time slice**, is defined (generally from 10 to 100 milliseconds)
- The ready queue is treated as a **circular queue**
- The CPU scheduler goes around the ready queue, allocating the CPU to each process for a time interval of up to 1-time quantum.

![[../../../../Attachments/Untitled 9 7.png|Untitled 9 7.png]]

![[../../../../Attachments/Untitled 10 7.png|Untitled 10 7.png]]

## Multi-level Queue Scheduling

### Multi-level Queue

- A class of scheduling algorithms has been created for situations in which processes are easily classified into different groups
- **Ready queue is partitioned into separate queues:**
    - Foreground (interactive)
    - Background (batch)
- **Each queue has its own scheduling algorithm**
    - **Foreground**: RR
    - **Background**: FCFS
- Scheduling must be done between the queues
    - **Fixed priority scheduling**: serve all from the foreground then from the background; the possibility of starvation
    - **Time slice:** each queue gets a certain amount of CPU time which it can schedule amongst its processes; i.e., 80% to foreground in RR / 20% to background in FCFS

![[../../../../Attachments/Untitled 11 7.png|Untitled 11 7.png]]

A multilevel queue scheduling algorithm partitions the ready queue into several separate queues

- The processes are permanently assigned to one queue, generally based on some property of the process, such as memory size, process priority, or process type.
- **Each Queue has its own scheduling algorithm.**

## Multilevel Feedback Queue

![[../../../../Attachments/Untitled 12 6.png|Untitled 12 6.png]]

Multilevel feedback queues

- A multilevel feedback-queue scheduling algorithm allows a process to move between queues.
    - The idea is to separate processes according to the characteristics of their CPU bursts.
    - If a process **uses too much CPU time,** it will be **moved to a lower-priority queue.**
- The multilevel-feedback-queue scheduler is defined by the following parameters:
    - Number of queues
    - Scheduling algorithms for each queue
    - Method used to determine when to upgrade a process
    - Method used to determine when to demote a process
    - Method used to determine which queue a process will enter when that process needs service.

## Thread Scheduling

- The distinction between user-level and kernel-level threads
- When threads are supported, threads are scheduled, not processes
- Many-to-one and many-to-many models, thread library schedules user-level threads to run on LWP.