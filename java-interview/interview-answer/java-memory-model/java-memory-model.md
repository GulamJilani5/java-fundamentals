## ➡️ 1. Explain Garbage Collection (GC) in Java and different GC algorithms.

- Garbage Collection in Java is an automatic process managed by the JVM to reclaim memory from objects in the Heap that are no longer in use, preventing memory leaks.
- An object becomes garbage when it’s no longer referenced, like when a variable is set to null or goes out of scope.
- The Garbage Collector works by marking reachable objects, sweeping away the unreachable ones, and sometimes compacting memory to reduce fragmentation.

### 🟦 Several GC algorithms, each suited for different needs:

##### 🔵 Serial GC:

Uses a single thread, suitable for small applications but causes longer pauses. It’s simple but not ideal for high-performance systems.

##### 🔵 Parallel GC:

Uses multiple threads to speed up collection, optimizing for throughput. It’s good for applications where performance is key, but it still has noticeable pauses.

##### 🔵 G1 (Garbage-First) GC:

Divides the Heap into regions and prioritizes collecting the most garbage-filled ones. It balances throughput and low latency, making it ideal for large applications. It’s the default since Java 9.

##### 🔵 ZGC and Shenandoah GC:

These are low-latency collectors designed for large-scale applications. They minimize pauses (often under 10ms) by working concurrently with the application, perfect for real-time systems.

### 🟦 Key Points to Emphasize:

- GC frees developers from manual memory management, reducing errors like memory leaks.
- Mention "stop-the-world" pauses as a trade-off and how modern GCs (like G1, ZGC) minimize them.
- **Example:** "If I create an object and lose all references to it, like setting a variable to null, the GC will eventually reclaim it. But if I accidentally keep a reference in a List, it won’t be collected, which could cause a memory leak."
- **Show understanding:** "The JVM tunes GC behavior based on the algorithm and application needs, but we can also suggest GC with System.gc(), though it’s not guaranteed to run."

### 🟦 Tips for Understanding:

- Think of GC as a cleanup crew for the Heap, only removing objects no one is using.
- Remember that GC only applies to the Heap, not the Stack or Metaspace.
- Practice explaining the trade-offs: Serial (simple, slow), Parallel (fast, high throughput), G1 (balanced), ZGC/Shenandoah (low latency).
- Visualize the Heap as a room full of boxes (objects), with the GC removing boxes that no one points to.

## ➡️ 2. How does Java memory model (JVM memory areas: heap, stack, metaspace) work?

### 🟦 Memory Management in Java

- The Java Memory Model is how the JVM organizes memory to run a Java program efficiently.
- It divides memory into three main areas: the Heap, Stack, and Metaspace
- This structure ensures Java programs are memory-efficient, thread-safe, and robust, with the JVM handling most of the complexity automatically.

##### 🔵 Heap

This is where all objects, like arrays or class instances, are stored. It’s shared across all threads and divided into the Young Generation for new objects and the Old Generation for long-lived objects. The Garbage Collector manages the Heap to free up memory from unused objects.

##### 🔵 Stack

This is used for method execution. Each thread has its own Stack, which stores stack frames containing local variables and method call information. When a method finishes, its frame is removed, making the Stack very fast and efficient.

##### 🔵 Metaspace

This stores class metadata, like class definitions and method information. It replaced PermGen in Java 8 and grows dynamically to avoid memory issues.

### 🟦 Key Points to Emphasize:

- The Heap is for objects, the Stack is for method calls, and Metaspace is for class metadata.
- Mention that the **Heap** is shared across threads, but each thread has its own Stack.
- Highlight that the **Garbage Collector** manages the Heap, which you’ll cover in the next question.
- **Example:** "For instance, if I create a String s = "Hello", the string object lives in the **Heap**, the variable s is stored in the **Stack**, and the String class definition is in Metaspace."

### 🟦 Tips for Understanding:

- Visualize the **Heap** as a big, shared storage space, the **Stack** as a per-thread notepad, and **Metaspace** as a filing cabinet.
- Remember that the **Heap** is where **Garbage Collection** happens, while the **Stack** is automatically managed (frames are removed when methods end).
- Practice drawing a diagram: a big box for the **Heap** (split into **Young/Old**), a stack of frames for the **Stack**, and a separate box for **Metaspace**.

## ➡️ 3. Java memory leak

- Java Memory Leak - The Silent Performance
- Have you ever deployed a Java application that runs fine for hours... but then suddenly slows down, eats all the RAM, and eventually crashes with an OutOfMemoryError? That's often a memory leak.

### 🟦 What is a Memory Leak in Java?

- A memory leak happens when objects are no longer needed but are still referenced (directly or indirectly).
- Preventing the **Garbage Collector (GC)** from cleaning them up.

##### 🔵 Over the time, this causes

- Increasing heap usage
- Slower response times
- Crashes in production

##### 🔵 Common Causes

- Static references that hold onto large objects.
  - **Example to avoid:** `public static List<User> users = new ArrayList<>();`
- Unclosed resources (DB connections, streams, sockets).
- Listeners & Callbacks not deregistered.
- Poorly implemented caches (growing forever).
- ThreadLocal misuse.

##### 🔵 How to Detect

- **Monitoring tools:** VisualVM, JConsole, Java Mission Control.
- **Heap dump analysis:** Eclipse MAT (Memory Analyzer Tool).
- **APM tools:** AppDynamics, Dynatrace, New Relic.

##### 🔵 Best Practices to Avoid Memory Leaks.

- Always close connections (try-with-resources). -Use WeakReference where applicable(eg: Map<Integer, String>  
   weakMap = new WeakHashMap<>();).
- Limit cache size with eviction policies.
- Remove unused listeners.
- Monitor your heap regularly.

## ➡️ 4. log.info("Hello: {}", name); VS log.info("Hello: "+ name);

- Use log.info("Hello: {}", name); Avoid: X Use log.info("Hello: "+ name);
- The **+** creates a new string every time, wasting memory. The **{}** syntax is lazy and only builds the string if the log is actually printed.
- **Memory Usage Impact:** This simple switch reduces unnecessary object creation, which in turn reduces garbage collection pressure, leading to a smoother application.

### 🟦 Few more Java memory management best practices

##### 🔵 Use StringBuilder / StringBuffer instead of + in loops

```java
// Avoid ❌
String result = "";
for (int i = 0; i < 1000; i++) {
    result += i;  // creates new String every time
}

// Better ✅
StringBuilder result = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    result.append(i);
}

```

- 👉 Prevents creation of hundreds/thousands of temporary strings.

##### 🔵 Reuse objects where possible

- Don’t create unnecessary wrappers like new Integer(5) (always use Integer.valueOf(5) or autoboxing).
- For heavy objects, consider object pooling (e.g., database connections via a pool).

##### 🔵 Be mindful of collections

- Pre-size collections if you know the size:

```java
new ArrayList<>(1000); // avoids frequent resizing

```

- Remove references from collections once no longer needed (to prevent memory leaks).

```java
List<String> data = new ArrayList<>();
// Process data
data.clear(); // or data = null;
```

##### 🔵 Avoid holding onto large objects longer than needed

- Null out references after use if the object is huge and won’t be reused.
- Be careful with static variables — they can accidentally cause memory leaks.

##### 🔵 Close Resources Properly

- Always close resources like streams, database connections, or file handles using `try-with-resources` to ensure they are released promptly. Unclosed resources can hold memory until garbage collection occurs.

- **Impact:** Prevents memory leaks and ensures resources are freed immediately.

```java
// Use try-with-resources
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    // Process file
}

```

##### 🔵 Use Primitive Types Over Wrapper Classes

- Prefer primitive types (e.g., int, double) over their wrapper classes (e.g., Integer, Double) when possible, as wrappers consume more memory due to object overhead.

- **Impact:** Reduces memory usage and avoids autoboxing/unboxing overhead.

```java
// Avoid
Integer sum = 0;
for (Integer i = 0; i < 1000; i++) {
    sum += i;
}
// Use
int sum = 0;
for (int i = 0; i < 1000; i++) {
    sum += i;
}
```
