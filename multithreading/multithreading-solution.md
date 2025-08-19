️✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ ••‣⁎⁕⁜※⁂

# ⏺️ Multithreading Resolution

## ➡️ Synchronization

- Lock-based (uses intrinsic locks / monitors).
- 🔴Provides both **mutual exclusion (atomicity)** + **visibility** guarantees
- 🔴Only thread enters the block at a time.
- Method level (instance or static).
- Block level (synchronized block within a method).
- Cannot be applied at class level directly (but can synchronize static methods for class-level locks).

##### Use Case

- 🔴When you need to protect a critical section involving multiple operations and shared state.
- **Example:** transferring money between two accounts.

#### 🟦 Synchronized Methods:

```java
class Counter {
    private int count = 0;
    public synchronized void increment() {
        count++; // Thread-safe
    }
}
```

#### 🟦 Synchronized Blocks:

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

#### 🟦 Synchronized Keyword:

- Ensures only one thread accesses the synchronized resource at a time.
- Uses the object’s intrinsic lock (monitor).

## ➡️ Thread Safety

Thread safety ensures that shared data remains consistent across threads without corruption.

#### 🟦 Thread-Safe Classes:

- **Collections:** Use Collections.synchronizedList() or CopyOnWriteArrayList for thread-safe collections.
- **StringBuilder vs. StringBuffer:** StringBuffer is thread-safe; StringBuilder is not.
- **Concurrent Utilities:** Use ConcurrentHashMap, BlockingQueue, etc., for high-performance thread safety.

#### 🟦 Volatile Keyword:

- Ensures 🔴**visibility** of variable changes across threads without guaranteeing atomicity.
- Lock free
- Used with variables(**eg.** 🔴 flags and state variables)

```java
class Shared {
    private volatile boolean flag = false;
    public void setFlag() { flag = true; }
    public boolean isFlag() { return flag; }
}
```

- Does not guarantee atomicity (e.g., i++ still needs synchronization).

#### 🟦 Atomic Classes:

- 🔴Provides lock-free, thread-safe operations on single variables using low-level CPU instructions (e.g., Compare-and-Swap).
- Provides both visibility & atomicity for single variables.
- 🔴Variable level (eg. Counters, Accumulators)
- Used with Wrappers not primitives(**e.g.** with Integer not int)
- Faster than synchronized in most cases.

```java
import java.util.concurrent.atomic.AtomicInteger;
class Counter {
    private AtomicInteger count = new AtomicInteger(0);
    public void increment() {
        count.incrementAndGet(); // Thread-safe atomic operation
    }
}
```

- Classes like `AtomicInteger`, `AtomicLong` `AtomicReference` provide lock-free, thread-safe operations.

#### 🟦 ReentrantLock:

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
