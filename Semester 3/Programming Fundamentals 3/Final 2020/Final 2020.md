![[../../../Attachments/2022_02_01_10_12_AM_Office_Lens.jpg]]

![[../../../Attachments/2022_02_01_10_12_AM_Office_Lens_(1).jpg]]

  

==**Exercise 4 - Semaphores:**==

```
public class BlockingQueue<T> implements BoundedBuffer<T> {
	private final Queue<T> queue = new LinkedList<T>();
	private final int capacity;
	private final Semaphores full, empty, mutex;
	
	public BlockingQueue(int capacity) {
		this.capacity = capacity;
		full = new Semaphores(0);
		empty = new Semaphores(capacity);
		mutex = new Semaphores(1);
	}

	public void put(T item) throws InteruptedException {
		empty.acquireUninterruptibly();
		try {
			mutex.aquireUninterruptibly();
		}	catch (InteruptedException ex) {
			empty.release();
			throw ex;
		}

		try {
			queue.add(item);
		} catch (RuntimeException ex) {
			empty.release();
			throw ex;
		} finally {
			mutex.release();
		}
		full.release();
	}

	public T take() throws InteruptedException {
		full.acquireUninterruptibly();
		try {
			mutex.aquireUninterruptibly();
		} catch(InteruptedException ex) {
			full.release();
			throw ex;
		}

		try {
			T temp = queue.remove();
			empty.release();
			return temp;
		} catch (RuntimeException ex) {
			full.release();
			throw ex;
		} finally {
			mutex.release();
		}
	}

}
```

**Exercise 5 - ReentrantLock Locks**

```
public class MyStack<T> {
	private final LinkedList<T> list = new LinkedList<>();
	private final Lock lock = new ReentrantLock();
	
	public void push(T element) {
		lock.lock();
		try {
			list.push(element);
		} finally {
			lock.unlock();
		}
	}
	
	public T pop() {
		lock.lock();
		try {
			T t = list.pop();
			return t;
		}finally {
			lock.unlock();
		}
	}
	
	public T peek() {
		lock.lock();
		try {
			T t = list.peek();
			return t;
		} finally {
			lock.unlock();
		}
	}
	
	public boolean empty() {
		lock.lock();
		try {
			return list.size() == 0;
		} finally {
			lock.unlock();
		}
	}

}
```

  

**Exercise 6 - Thread Pools**

```
// TODO(1):
ExecutionService threadpool = Execution.newFixedThreadPools(N_THREADS);

// TODO(2.1):
SequentialArraySumWorker s = new SequentialArraySumWorker(array, low, high);

// TODO(2.2):
results.add(threadpool.submit(s));

//TODO(3):
for (Future<long> i : results) {
	results += i.get();
}

//TODO(4):
threadpool.shutdown();
```