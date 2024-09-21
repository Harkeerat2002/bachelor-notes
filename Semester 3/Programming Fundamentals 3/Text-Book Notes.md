# Chapter 1: Introduction

A `thread` is a flow of execution through the process code.

## 1.2 Benefits of Threads

- Threads can reduce development and maintenance costs, and improve the performance of complex applications.
- Threads are useful in GUI applications for improving the responsiveness of the user interface, and in server applications for improving resource utilization and throughput.

### 1.2.1. Exploiting Multiple Processors

- Multiprocessor systems used to be expensive and rare, however today they are cheap. This trend will continue as it gets harder to scale up clock rates, processor manufactures will instead put more processor cores on a single chip.
- Using multiple threads can also help achieve better throughput on single-processor systems. If a program is single-threaded, the processor remains idle while it waits for a synchronous I/O operation to complete.

## 1.3. Risks of Threads

### 1.3.1. Safety Hazards

- Threads safety could have unpredictable and sometimes surprising ordering of operations in multiple threads, due to the absence of sufficient synchronization.

**Example:**

```
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

### 1.3.2 Liveness Hazards

- Liveness means that "something good eventually happens"
- A liveness failure occurs when an activity gets into a state such that it is permanently unable to make forward progress.
- One form of liveness failure that can occur in sequential programs is an inadvertent infinite loop, where the code that follows the loop never gets executed.

# Chapter 2: Thread Safety

- Shared variables are variables that could be accessed by multiple threads; by mutable, it is meant that its value could change during its lifetime.
- Whether an object needs to be thread-safe depends on whether it will be accessed from multiple threads.
- Whenever more than one thread accesses a given state variable, and one of them might write to it, they all must coordinate their access to it using synchronization. The primary mechanism for synchronization in Java is the `synchronized` keyword, which provides exclusive locking, but the term `synchronization` also includes the use of `volatile` variable, explicit locks, and atomic variables.
- If multiple threads access the same mutable state variable without appropriate synchronization, the program is broken. There are three ways to fix it:
    - Don't share the state variable across threads;
    - Make the state variable immutable; or
    - Use synchronization whenever accessing the state variable

## 2.1. What is Thread Safety?

- A reasonable definition of **thread safety** is the concept of correctness.
- **Correctness** means that a class conforms to its specification. A good specification defines invariants constraining an object's state and post - conditions describing the effects of its operations.
- A class is **thread-safe** if it behaves correctly when accessed from multiple threads, regardless of the scheduling or interleaving of the execution of those threads by the runtime environment, and with no additional synchronization or other coordination on the part of the calling code.

### 2.1.1. Example: A Stateless Servlet

```
@ThreadSafe
public class StatelessFactorizer implements Servlet {
	public void service(ServletRequest reg, ServletResponse resp) {
		BigInteger i = extractFormRequest(req);
		BigInteger[] factors = factor(i);
		encodeIntroResponse (resp, factors);
	}
}
```

- `Statelessfactorizer` is, like most servlets, **stateless:** it has no fields and references no fields from other classes.
- **Stateless** object are always thread-safe.

## 2.2. Atomicity

```
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

### 2.2.1. Race Conditions

`UnsafeCountingFactorizer` has several race conditions that make its results unreliable. A race condition occurs when the correctness of a computation depends on the relative timing or interleaving of multiple threads by the runtime; in other words, when getting the right answer relies on lucky timing.

### 2.2.2. Example: Race Conditions in Lazy Initialization

A common idiom that uses check-then-act s lazy initialization. The goal of lazy