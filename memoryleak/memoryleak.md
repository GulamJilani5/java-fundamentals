✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ • • ‣ ⁎ ⁕ ⁜ ※ ⁂

# ⏺️ Java Memory Leak - The Silent Performance

Have you ever deployed a Java application that runs fine for hours... but then suddenly slows down, eats all the RAM, and eventually crashes with an `OutOfMemoryError`? That's often a memory leak.

## ➡️ What is a Memory Leak in Java?

A memory leak happens when objects are no longer needed but are still referenced (directly or indirectly) - preventing the `Garbage Collector (GC)` from cleaning them up.

### 🟦 Over the time, this causes:

- Increasing heap usage
- Slower response times
- Crashes in production

### 🟦 Common Causes

- Static references that hold onto large objects
  - **Example to avoid:-** `public static List<User> users = new ArrayList<>();`
- Unclosed resources (**DB connections, streams, sockets**).
- **Listeners & Callbacks** not deregistered.
- Poorly implemented caches (growing forever).
- ThreadLocal misuse.

### 🟦 How to Detect

- **Monitoring tools:** VisualVM, JConsole, Java Mission Control.
- **Heap dump analysis:** Eclipse MAT (Memory Analyzer Tool).
- **APM tools:** AppDynamics, Dynatrace, New Relic.

### 🟦 Best Practices to Avoid Memory Leaks

- Always close connections (try-with-resources).
- Use WeakReference where applicable.
  - **eg:** `Map<Integer, String> weakMap = new WeakHashMap<>();.`
- Limit cache size with eviction policies.
- Remove unused listeners.
- Monitor your heap regularly.
