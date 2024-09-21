# Theads

## Runnable

```
package java.lang;
@FunctionalInterface
public interface Runnable {
	// When an object implementing interface Runnable is used to create a
	// thread, starting the thread causes the object's run method to be called
	// in that separately executing thread
	abstract void run();
}
```

```
package java.lang;
public class Thread implements Runnable {
	// Allocates a new Thread object
	public Thread()

	// Allocates a new Thread object setting the name received in the argument
	public Thread(String name)

	// Allocates a new Thread object. target is the Runnable object whose run
	// method is invoked when this thread is started
	public Thread(Runnable target)

	// Allocates a new Thread object. target is a Runnable object and name
	// is a name for the thread
	public Thread(Runnable target, String name)
}
```

```
package java.lang;
public class Thread implements Runnable {
	// This method invokes run()
	public void start()
	// This method is called when execution of the thread begins
	public void run()
	
	// Returns a handle to the running thread
	public static Thread currentThread()
...}
```

```
package java.lang;
public class Thread implements Runnable {
	// Returns the name of the thread
	public final void getName()
	// Changes the name of this thread to be equal to the argument
	public final void setName(String name)
...}
```

```
package java.lang;
public class Thread implements Runnable {
	// Waits for this thread to die (equal to use join(0))
	public final void join() throws InterruptedException
	
	// Waits at most millis milliseconds for this thread to die. A timeout of
	// 0 means to wait forever
	public final void join(long millis)
																throws InterruptedException
	
	// Waits at most millis milliseconds plus nanos nanoseconds for this
	// thread to die
	public final void join(long millis, int nanos)
																throws InterruptedException
...}
```

```
package java.lang;
public class Thread implements Runnable {
	// Indicates that this thread is willing to give up the processor.
	// Not guaranteed to behave this way
	public static void yield()

	// Cease execution for some time (like join(..) depends on OS timing)
	public static void sleep(long millis) throws InterruptedException
	
	// Control relatively how often a thread is selected for execution
	public final void setPriority(int newPriority)
...}
```

### Implementing Runnable

```
class MyRunnable implements Runnable {
	@Override
	public void run() {
		System.out.println(Thread.currentThread().getName());
	}
}
public class ThreadExample2 {
	public static void main(String[] args) {
		Thread t1 = new Thread(new MyRunnable(), "T1");
		Thread t2 = new Thread(new MyRunnable(), "T2");
		t1.start();
		t2.start();
	}
}
```

### Interrupts

```
package java.lang;
public class Thread implements Runnable {

	// Interrupts this thread
	public void interrupt()
	
	// Tests whether the current thread has been interrupted. The interrupted
	// status of the thread is cleared by this method
	public static boolean interrupted()
	
	// Tests whether this thread has been interrupted. The interrupted status
	// of the thread is unaffected by this method
	public boolean isInterrupted()
...}
```

## Extending Thread

```
class MyThread extends Thread {
	public MyThread(String name) {
		super(name);
	}
	@Override
	public void run() {
		System.out.println(this.getName());
	}
}
public class ThreadExample1 {
	public static void main(String[] args) {
		Thread t1 = new MyThread("T1");
		Thread t2 = new MyThread("T2");
		t1.start();
		t2.start();
	}
}
```

# Thread-Local:

```
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

# Semaphore:

```
package java.util.concurrent;
public class Semaphore implements java.io.Serializable {
	// Creates a Semaphore with the given number of
	// permits and nonfair fairness setting
	public Semaphore(int permits)
	
	// Creates a Semaphore with the given number of
	// permits and the given fairness setting
	public Semaphore(int permits, boolean fair)
...}
```

```
package java.util.concurrent;
public class Semaphore implements java.io.Serializable {
	// Acquires a permit from this semaphore, blocking until one is
	// available, or the thread is interrupted
	public void acquire() throws InterruptedException

	// Acquires a permit from this semaphore, only if one is
	// available at the time of invocation
	public boolean tryAcquire()

	// Releases a permit, returning it to the semaphore, increasing
	// the number of available permits by one
	public void release()
...}
```

```
package java.util.concurrent;
public class Semaphore implements java.io.Serializable {
// Acquires a permit from this semaphore, blocking until one is available.
// Acquires a permit, if one is available and returns immediately, reducing
// the number of available permits by one. If no permit is available then
// the current thread becomes disabled for thread scheduling purposes and
// lies dormant until some other thread invokes the release() method for
// this semaphore and the current thread is next to be assigned a permit
public void acquireUninterruptibly()

...}
```

# Synchronized Blocks:

```
synchronized (myObject) {
// Lock is held
...
}
// Lock is released
```

![[../../../Attachments/Untitled 38.png|Untitled 38.png]]

# Producer/Consumer Queues with Semaphores:

```
public class Queue {
	private int in, out;
	private final long[] buffer;
	private final Semaphore nonEmpty, nonFull, manipulation;
	
	public Queue(int size) {
		in = out = 0;
		buffer = new long[size];
		nonEmpty = new Semaphore(0);
		nonFull = new Semaphore(size);
		manipulation = new Semaphore(1);
	}
	
	public void enqueue(long x) {
		nonFull.acquireUninterruptibly();
		manipulation.acquireUninterruptibly();
		try {
			doEnqueue(x);
		}
		finally {
			manipulation.release();
			nonEmpty.release();
		}
	}

	public void dequeue(long x) {
		nonEmpty.acquireUninterruptibly();
		manipulation.acquireUninterruptibly();
		try {
			doDequeue(x);
		}
		finally {
			manipulation.release();
			nonFull.release();
		}
	}



}
```

# Object:

### Wait

```
package java.lang;
public class Object {
	// Waits to be notified by another thread (equal to use wait(0))
	public final void wait() throws InterruptedException
	
	// Causes the current thread to wait until another thread invokes
	// notify() or notifyAll() for this object
	public final void wait(long timeout) throws InterruptedException
...}
```

### Notify

```
package java.lang;
public class Object {
	// Wakes up a single thread that is waiting on this object's lock
	public final void notify()
	
	// Wakes up all threads that are waiting on this object's lock
	public final void notifyAll()
...}
```