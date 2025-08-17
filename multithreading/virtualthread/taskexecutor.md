✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ ••‣⁎⁕⁜※⁂

# ⏺️ Executor Services

## ➡️ Executor

- It is high level concurrency utility
- It abstract away the complexity of thread management, making usage of threads easier.
- Provides a way to manage and execute task asynchronously in a pool of threads.

## ➡️ ExecutorService

A more powerful version of `Executor`. It extends `Executor` and adds features like shutting down threads, running tasks that return results, and managing multiple tasks.

Imagine you're a chef in a busy kitchen. Instead of cooking every dish yourself (like creating a new thread for each task), you hire a team of **cooks** (a **thread pool**) and assign them **dishes** (**tasks**). The `ExecutorService` is like your kitchen manager—it assigns tasks to available cooks, reuses them, and ensures the kitchen runs smoothly without hiring too many cooks (creating too many threads).

##### 🟦 Key Methods in ExecutorService

- `submit(Runnable task)` → runs a task without return value.
- `submit(Callable<T> task)` → runs a task that returns a Future<T>.
- `invokeAll(Collection<? extends Callable<T>> tasks)` → run multiple tasks in parallel, wait for all.
- `invokeAny(Collection<? extends Callable<T>> tasks)` → run multiple tasks, return result of first one completed.
- `shutdown()` → stop accepting new tasks, let current tasks finish.
- `shutdownNow()` → try to stop all running tasks immediately.

### 🟦 What problem does ExecutorService resolve

#### 🔵 Avoids Thread Creation Overhead:

Creating a new thread for each task is slow and uses a lot of memory. ExecutorService reuses threads from a pool.

#### 🔵 Simplifies Thread Management:

You don’t need to manually start, stop, or track threads.

#### 🔵 Handles Task Queuing:

If there are more tasks than threads, ExecutorService queues them and processes them when a thread is free.

#### 🔵 Supports Task Results:

Unlike basic threads, ExecutorService can run tasks that return results (using Callable).

#### 🔵 Prevents Resource Overload:

Limits the number of threads to avoid crashing your program.

#### 🔵 Enables Asynchronous Execution:

Tasks run in the background, so your main program doesn’t wait.

### 🟦 Types of ExecutorService

#### 🔵 SingleThreadExecutor

- Uses one thread to run tasks one at a time, in order.
- **Good for:** Sequential tasks, like processing a queue of events.
- **Example:** `Executors.newSingleThreadExecutor()`.

#### 🔵 FixedThreadPool

- A pool with a fixed number of threads (e.g., 3 threads).
- If all threads are busy, new tasks wait in a queue.
- **Good for:** Applications with a steady number of tasks, like a web server handling client requests.
- **Example:** `Executors.newFixedThreadPool(3)` creates a pool with 3 threads.

#### 🔵 CachedThreadPool

- Creates new threads as needed and reuses idle ones. Idle threads are removed after 60 seconds.
- **Good for:** Short, unpredictable tasks, like handling sudden bursts of user requests.
- **Example:** `Executors.newCachedThreadPool()`.

#### 🔵 ScheduledThreadPool

- Runs tasks after a delay or at regular intervals (like a timer).
- **Good for:** Periodic tasks, like checking for updates every 5 seconds.
- **Example:** `Executors.newScheduledThreadPool(2)`.

#### 🔵 WorkStealingPool

- Uses multiple threads (based on CPU cores) where idle threads “steal” tasks from busy ones.
- **Good for:** Tasks that split into smaller subtasks, like parallel processing.
- **Example:** `Executors.newWorkStealingPool()`.
