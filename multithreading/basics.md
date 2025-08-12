🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️⏺️
☑️ • ‣ → ⁕

# ➡️ 1. Threads and Creating Thread

## 🟦 Threads

- Threads are lightweight processes within a program that allow multiple tasks to run concurrently, utilizing CPU resources efficiently.
- Threads share the same memory space, enabling communication but requiring careful synchronization.

## 🟦 Creating Thread

- Primary two ways to create the thread

### 🔵 Extending the Thread Class

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running: " + Thread.currentThread().getName());
    }
}
public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start(); // Starts the thread
    }

}
```

- Override the `run()` method to define the thread's task.
- Call `start()` to initiate the thread (not `run()` which executes in the current thread).

### 🔵 Implementing the Runnable Interface (Preferred):

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable running: " + Thread.currentThread().getName());
    }
}
public class Main {
    public static void main(String[] args) {
        Thread thread = new Thread(new MyRunnable());
        thread.start();
    }
}
```

- More flexible, as it allows the class to extend another class.
- Pass the Runnable object to a Thread constructor.

# ➡️ 2. Thread Lifecycle

## A thread in Java goes through several states:

### New:

Thread is created but not started (`new Thread()`).

### Runnable:

Thread is ready to run after `start()` is called; it’s waiting for CPU time.

### Running:

Thread is executing its `run()` method.

### Blocked/Waiting:

##### Blocked:

Thread is waiting for a monitor `lock` (e.g., in a synchronized block).

##### Waiting:

Thread is waiting indefinitely (e.g., `wait()`, `join()`, or `LockSupport.park()`).

##### Timed Waiting:

Waiting with a timeout (e.g., `sleep()`, `wait(timeout)`, or `join(timeout)`).

### Terminated:

Thread has completed execution or was stopped.

## Transitions:

- **start():** New → Runnable.
- **Scheduler assigns CPU:** Runnable → Running.
- **sleep(), wait(), or I/O:** Running → Blocked/Waiting/Timed Waiting.
- **notify() or lock release:** Blocked/Waiting → Runnable.
- **run() completes or exception:** Running → Terminated.

## ➡️ 3. Synchronization

- Synchronization prevents thread interference and ensures data consistency when multiple threads access shared resources.

### Synchronized Methods:

```java
class Counter {
    private int count = 0;
    public synchronized void increment() {
        count++; // Thread-safe
    }
}
```

### Synchronized Blocks:

```java
class Counter {
    private int count = 0;
    public synchronized void increment() {
        count++; // Thread-safe
    }
}

```

- Locks the entire object (instance methods) or class (static methods).

- More granular, locking only specific code sections.
- Reduces contention compared to synchronized methods.

### Synchronized Keyword:

- Ensures only one thread accesses the synchronized resource at a time.
- Uses the object’s intrinsic lock (monitor).

## ➡️ 4. Thread Safety

Thread safety ensures that shared data remains consistent across threads without corruption.

### 🟦 Thread-Safe Classes:

- **Collections:** Use Collections.synchronizedList() or CopyOnWriteArrayList for thread-safe collections.
- **StringBuilder vs. StringBuffer:** StringBuffer is thread-safe; StringBuilder is not.
- **Concurrent Utilities:** Use ConcurrentHashMap, BlockingQueue, etc., for high-performance thread safety.

### 🟦 Volatile Keyword:

- Ensures visibility of variable changes across threads without guaranteeing atomicity.

```java
class Shared {
    private volatile boolean flag = false;
    public void setFlag() { flag = true; }
    public boolean isFlag() { return flag; }
}
```

- Does not guarantee atomicity (e.g., i++ still needs synchronization).

### 🟦 Atomic Classes:

- Provides lock-free, thread-safe operations on single variables using low-level CPU instructions (e.g., Compare-and-Swap).

```java
import java.util.concurrent.atomic.AtomicInteger;
class Counter {
    private AtomicInteger count = new AtomicInteger(0);
    public void increment() {
        count.incrementAndGet(); // Thread-safe atomic operation
    }
}
```

- Classes like `AtomicInteger`, `AtomicReference` provide lock-free, thread-safe operations.

### 🟦 ReentrantLock:

- A flexible, explicit locking mechanism that provides more control than synchronized.

```java
import java.util.concurrent.locks.ReentrantLock;
class Counter {
    private int count = 0;
    private final ReentrantLock lock = new ReentrantLock();
    public void increment() {
        lock.lock();
        try {
            count++;
        } finally {
            lock.unlock();
        }
    }
}
```

- More flexible than synchronized (e.g., supports try-lock, fairness).
- Requires explicit `lock()` and `unlock()` (use finally to avoid deadlocks).
