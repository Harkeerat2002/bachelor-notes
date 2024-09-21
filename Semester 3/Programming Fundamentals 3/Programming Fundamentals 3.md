[Semester:: 3]   •   [Year:: 2]   •   [ECT:: 6]• [Completed:: ✅]
# Questions / Doubts
- [[QuestionsDoubts]]
# Assignments
- [[Class Notes/Programming Fundamentals 3/Assignment 1|Assignment 1]]
# Text-Book Notes:
- [[Text-Book Notes]]
# Syntax:
- [[Syntax for the Concepts]]
# Practice:
- [[Final 2020]]
# Lecture 1: Concurrency Motivation
## Amdahl's Law

- Amdahl's law is a formula which gives the theoretical speedup in latency of the execution of a task (for a fixed workload) that can be expected for a system whose resources are improved.
    - In parallel computing, the resources are the processors
    - Amdahl's law helps predict the theoretical speedup when using multiple processors
- Only a fraction of the time required to run an application can benefit from parallelization

$$T_n = T_s + (\frac{T_p}{n})$$

- $T_n$﻿: execution time on _n_ processors
- $T_s$﻿: sequential component (cannot be parallelized)
- $T_p$﻿: parallel component (can benefit from multiprocessors)

**Speedup:**

$$S_n = \frac{T_1}{T_n}$$

- Compares the latency for solving the identical computational problem on one hardware unit versus on n hardware units
- $\frac{T_1}{T_n}$﻿ is limited by $T_s$﻿
    - If $n \to \infty$﻿, then $T_n \to T_s$﻿

**Parallel Efficiency:**

$E_n = \frac{S_n}{n}$

- $S_n$﻿: the speedup on n processors
- The parallel efficiency is often used to measure the return on hardware investment
- A program that scales linearly ($S_n = n)$﻿ has a parallel efficiency of 1

**Exercise Example:**
[[Exercise 1]] 

# Lecture 2: Processes and Threads

## Sequential Execution and Parallel Execution:

**Sequential Execution:**

- In **sequential execution** each statement in the source code is executed one at a time in sequential order
- A system is said to be **concurrent** if it can support two or more operations in progress at the same time.
- A system is said to be parallel if it can support two or more operations execution simultaneously

**Parallel Execution:**

- A system is said to be **parallel** if it can support two or more operations executing simultaneously
- In **parallel execution** there must be multiple computing units, so that two or more threads can execute code simultaneously (more on this later)
- “Parallel” is a subset of “concurrent”
    - A concurrent application may run code in parallel
    - In the absence of multiple computing units, concurrent applications cannot run  
        in parallel

## Synchronous Execution and Asynchronous Execution:

- **Synchronous execution** is a form of processing that waits for an operation to complete, potentially leaving system resources idle meanwhile
    - A synchronous operation blocks a process until the operation completes
- **Asynchronous execution** is a form of processing that permits other operations to continue before the current one has finished
    - An asynchronous operation is non-blocking and only initiates the operation
    - The next operation can be executed regardless of the completion status of the current operation

# Thread

**Runnable:**

```java
package java.lang
@FunctionalInteface
public interface Runnable {
	// When an object implementing interface Runnable is used to create a
	// thread, starting the thread causes the object's run method to be called
	// in that separately executing thread
	abstract void run();
}
```

**Thread:**

```java
package
```

# Lecture 3: Thread Safety

## Hazards:

### Safety Hazards

- Threads safety could have unpredictable and sometimes surprising ordering of operations in multiple threads, due to the absence of sufficient synchronization.

**Example:**

```java
@NotThreadSafe
public class unsafeSequence {
	private int value;
	
	/** Returns a unique value */
	public int getNext() {
		return value++;
	}
}
```

In the above example it can be seen the `unsafeSequence` is supposed to generate a sequence of unique integer values. However, this example in multiple threads could lead to undesirable results. The problem with `unsafeSequence` is that with some unlucky timing, two threads could call `getNext()` and receive the same value.

![[../../Attachments/Untitled.png|Untitled.png]]

The increment notation, `nextvalue++`, may appear to be a single operation, but is in fact three separate operations: read the value, add one to it, and write out the new value. Since operations in multiple threads may be arbitrarily interleaved by the runtime, it is possible for two threads to read the value at the same time, both see the same value, and then both add one to it. The result is that the same sequence number is returned from multiple calls in different threads.

### Liveness Hazards

- Liveness means that "something good eventually happens"
- A liveness failure occurs when an activity gets into a state such that it is permanently unable to make forward progress.
- One form of liveness failure that can occur in sequential programs is an inadvertent infinite loop, where the code that follows the loop never gets executed.

### Performance Hazards

- Liveness means “eventually progress will be made (at some point)”
- But parallel programming is aimed at performance
    - Multi-threaded applications can introduce performance overheads due to:
        - Frequent context switches
        - Thread scheduling
        - Inter-thread communication
        - Loss of locality
        - Synchronization overheads

## Atomicity

```java
@NotThreadSafe
public class UnsafeCountingFactorizer implements Servlet {
	private long count = 0;

	public long getCount() {
		return count;
	}

	public void service (ServletRequest reg, ServletResponse resp) {
		BigInteger i = extractFromRequest(req);
		BigInteger[] factors = factors(i);
		++count;
		encodeIntoResponse(resp, factors);
	}
}
```

`UnsafeCountingFactorizer` is not a thread-safe, even though it would work just fine in a single-threaded environment. It loses its updated overtime when it is running on multi-threads. While the increment operation, `++count`, may look like a single action because of its compact syntax, its is not Atomic, which means that it does not execute as a single, indivisible operation.

**Definition:**

**Atomicity:** If an operation done by computer is considered atomic if it is guaranteed to be isolated from other operations that may be happening at the same time.

Synchronization ensures atomicity, preventing one thread from modifying the state of an object when another thread is using it.

## Memory Visibility:

- **Visibility** ensures that the memory writes of one thread can be seen by another thread.
- In **multi-threaded**, there is no guarantee that a reading thread will see a value written by another thread.

## Sequential Consistency:

- It is a strong guarantee that is made about visibility and ordering in an execution of a program.
- Within a sequentially consistent execution, there is a total order over all individual actions, which is consistent with the order of the program, and each individual action is atomic and is immediately visible to every thread.
- However this is very expensive to implement.

## Java Memory Model:

- This maintains a **within-thread-as-if-serial** semantics.
- As long as the statements executed by a thread produce the same result as if they were executed in program order, all re-orderings are permitted

## Happen-Before Relation:

- An (inter-thread) action is an action performed by one thread that can be detected or directly influenced by an action performed in another thread

## Thread Safety:

- A reasonable definition of **thread safety** is the concept of correctness.
- **Correctness** means that a class conforms to its specification. A good specification defines invariants constraining an object's state and post - conditions describing the effects of its operations.
- A class is **thread-safe** if it behaves correctly when accessed from multiple threads, regardless of the scheduling or interleaving of the execution of those threads by the runtime environment, and with no additional synchronization or other coordination on the part of the calling code.

## Races:

- A **race condition** occurs when the correctness of a computation depends on the relative timing or interleaving of multiple threads by the runtime
- A **data race** arises when synchronization is not used to coordinate all access to a shared non-final field:
    - When one thread might read a field at the same moment while another thread writes to the ﬁeld.
    - When one thread might write to a field at the same moment while another thread also writes to the field

![[../../Attachments/Untitled 1.png|Untitled 1.png]]

- If multiple threads access the same mutable state variable without appropriate synchronization, the program is not thread-safe
- Some ways to fix this are:
    - Thread-local: do not share the state variable across threads
    - Immutable: make the state variable immutable
    - Synchronization: use synchronization **whenever** accessing the state variable

## Thread Local:

- ThreadLocal: associates a per-thread value with a value-holding object
- A means of enforcing thread confinement
    - Make an object accessible only by a single thread
- Provides getter and setter methods that maintain a separate copy of the value for each thread that uses it
    - A getter returns the most recent value passed to the setter by the currently executing thread
- Each thread holds an implicit reference to its copy of a thread-local variable
- After a thread terminates, all its thread-local instances are subject to garbage collection (assuming that an instance is not kept alive, e.g., a public static field referring to it)
- **Methods of Thread Local:**
    
    ```java
    package java.lang;
    public class ThreadLocal<T> {
    	// Returns the current thread's "initial value". This method will be
    	// invoked the first time a thread accesses the variable with the get()
    	// method, unless the thread previously invoked the set(T) method
    	protected T initialValue()
    	// Returns the value in the current thread's copy of this thread-local
    	// variable. If the variable has no value, initialValue() is called
    	public T get()
    	// Sets the current thread's copy of this thread-local variable to the
    	// specified value
    	public void set(T value)
    	
    	// Removes the current thread's value for this thread-local variable
    	public void remove()
    
    }
    ```
    
- **Example of Thread Local:**
    
    ```java
    public class ThreadId {
    	// Atomic integer containing the next thread ID to be assigned
    	private static final AtomicInteger nextId = new AtomicInteger(0);
    	// Thread local variable containing each thread's ID
    	private static final ThreadLocal<Integer> threadId =
    		new ThreadLocal<Integer>() {
    			@Override protected Integer initialValue() {
    				return nextId.getAndIncrement();
    		}
    	};
    	
    	// Returns the current thread's unique ID, assigning it if necessary
    	public static int get() {
    	return threadId.get();
    	}
    
    }
    ```
## Synchronization:

- A **critical section** (CS) is a portion of a program that uses a shared resource
    - Properties:
        - Mutual Exclusion (= Safety):
            - Only one thread can be inside the CS at a time
        - Progress (= Liveness)
            - If thread T is not in the critical section, then T cannot prevent another thread S from entering the critical section
        - Bounded Waiting (= no starvation)
            - If thread T is waiting on the critical section, then T will eventually enter the critical section
        - No assumptions on timing
            - Requirements must be met with any number of CPUs and must not rely on the underlying scheduler
- **Mutually Exclusive:** It means only one thread can execute at a time.
- **Thread synchronization** is as a mechanism ensuring that two or more concurrent threads do not simultaneously execute a critical section
- Mutual exclusion can be guaranteed by placing locks around critical sections
- A **lock** is a synchronization mechanism that at most one thread can own at a time to limit access to a shared resource
# Lecture 4: Semaphores and Monitors

## Semaphores:
- A **semaphore** is a variable or abstract data type used to control access to a common resource by multiple processes (or threads) in a concurrent system.
    - Every semaphore maintains a number of permits that restricts the number of threads accessing a shared resource
- **Counting semaphores** allow setting an arbitrary number of permits
- **Binary semaphores** have only one permit (“available”), and are used to implement locks (permit available = unlocked)
    - The entity holding the sole permit can access the critical section
- Semaphores implement three operations:
    - **Initialization** to a non-negative value
    - **Wait-** decrements semaphore value
        - Atomic Operations
    - **Signal-** increments the semaphore value.
        - Atomic Operations
- Semaphores ensures fairness.

## Bounded Buffer (Producer-Consumer Problem):

![[../../Attachments/Untitled 2.png|Untitled 2.png]]

- Assume a shared buffer (queue) of limited size
- Producer puts data into a queue:
    - Cannot add data unless space is free
- Consumer removes data:
    - Cannot remove data if queue is empty
- **Solution:**
    
    ![[../../Attachments/Untitled 3.png|Untitled 3.png]]
    
- **Semaphores Methods**
    
    ```java
    package java.util.concurrent;
    public class Semaphore implements java.io.Serializable {
    	// Creates a Semaphore with the given number of
    	// permits and nonfair fairness setting
    	public Semaphore(int permits)
    
    	// Creates a Semaphore with the given number of
    	// permits and the given fairness setting
    	public Semaphore(int permits, boolean fair)
    
    	// Acquires a permit from this semaphore, blocking until one is
    	// available, or the thread is interrupted
    	public void acquire() throws InterruptedException
    	// Acquires a permit from this semaphore, only if one is
    	// available at the time of invocation
    	public boolean tryAcquire()
    
    	// Releases a permit, returning it to the semaphore, increasing
    	// the number of avail
    	public void release()
    
    	// Acquires a permit from this semaphore, blocking until one is available.
    	// Acquires a permit, if one is available and returns immediately, reducing
    	// the number of available permits by one. If no permit is available then
    	// the current thread becomes disabled for thread scheduling purposes and
    	// lies dormant until some other thread invokes the release() method for
    	// this semaphore and the current thread is next to be assigned a permit
    	public void acquireUninterruptibly()
    ...}
    ```
    
- **Example of Semaphores:**
    
    ![[../../Attachments/Untitled 4.png|Untitled 4.png]]
    
    ![[../../Attachments/Untitled 5.png|Untitled 5.png]]
    
    ![[../../Attachments/Untitled 6.png|Untitled 6.png]]


## Monitors:  

### **Stateless Object:**

- Stateless object is an instance of a class without instance fields (instance variables). The class may have fields, but they are compile-time constants (static final).
- A very much related term is immutable. Immutable objects may have state, but it does not change when a method is invoked (method invocations do not assign new values to fields). These objects are also thread-safe.
- Stateless Objects are always thread safe.

 