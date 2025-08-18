`Executor ← ExecutorService ← ScheduledExecutorService`
All thread pools implement `ExecutorService` (and thus `Executor`), except `ScheduledExecutorService`, which is the interface itself.

## ➡️ Executor Interface

The simplest building block. It's an interface with just one method: execute(Runnable task).

- It is high level concurrency utility
- It abstract away the complexity of thread management, making usage of threads easier.
- Provides a way to manage and execute task asynchronously in a pool of threads.

## ➡️ ExecutorService Interface

A more powerful version of `Executor`. It extends `Executor` and adds features like shutting down threads, running tasks that return results, and managing multiple tasks.

Imagine you're a chef in a busy kitchen. Instead of cooking every dish yourself (like creating a new thread for each task), you hire a team of **cooks** (a **thread pool**) and assign them **dishes** (**tasks**). The `ExecutorService` is like your kitchen manager—it assigns tasks to available cooks, reuses them, and ensures the kitchen runs smoothly without hiring too many cooks (creating too many threads).

##### 🟦 Key Methods in ExecutorService

- `submit(Runnable task)` → runs a task without return value.
- `submit(Callable<T> task)` → runs a task that returns a Future<T>.
- `invokeAll(Collection<? extends Callable<T>> tasks)` → run multiple tasks in parallel, wait for all.
- `invokeAny(Collection<? extends Callable<T>> tasks)` → run multiple tasks, return result of first one completed.
- `shutdown()` → stop accepting new tasks, let current tasks finish.
- `shutdownNow()` → try to stop all running tasks immediately.

## ➡️ ScheduledExecutorService Interface
