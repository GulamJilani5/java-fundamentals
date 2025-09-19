⏺🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ 4. Explain HashMap internal working (hashing, collision handling, load factor).

### 🟦 Hashing the Key:

- Every key has a hashCode() method that generates a number (like a unique ID for the key).
- Java tweaks this number to make it better (to avoid clashes) and uses it to decide which bucket in the array the key-value pair should go into.
- **Simple analogy:** Imagine a library with 16 shelves (buckets). The key’s hash code determines which shelf (e.g., shelf #5) to place the book (key-value pair) on.

### 🟦 Finding the Bucket:

- The tweaked hash code is used to calculate an index (a number between 0 and the array size minus 1).
- **Formula:** index = hash % array_size (Java uses a bitwise trick, (n-1) & hash, for speed since the array size is a power of 2, like 16).
- This index points to a specific bucket in the array.

### 🟦 Storing the Key-Value Pair (put):

- Once the bucket is found, the key-value pair is stored there.
- If the bucket is empty, the pair is added as a node (a small object containing the key, value, hash, and a pointer to the next node).
- If the bucket already has entries (a collision), Java handles it by:
  - Adding the new pair to a linked list in that bucket (like stacking books on the same shelf).
  - In Java 8+, if the linked list gets too long (more than 8 entries), it turns into a balanced tree (like organizing books in a sorted order for faster searching).

### 🟦 Retrieving a Value (get):

- To find a value, Java hashes the key again to find the bucket.
- It then checks the bucket:
  - If it’s a single node, it compares the key (using equals()).
  - If it’s a linked list or tree, it searches through the entries to find a matching key.
  - If found, it returns the value; otherwise, it returns null.

### 🟦 Handling Collisions:

- Collisions happen when two keys hash to the same bucket (like two books assigned to the same shelf).
- Java uses a linked list (or a tree in Java 8+ for long lists) to store multiple pairs in the same bucket.
- When searching, it checks each entry in the list/tree using equals() to find the right key.

### 🟦 Resizing (When the Map Gets Full):

- The HashMap starts with 16 buckets (default) and a load factor of 0.75 (a threshold).
- If the number of entries exceeds 16 \* 0.75 = 12, the array doubles in size (to 32 buckets).
- All existing key-value pairs are rehashed (recalculated to new bucket indices) and moved to the new array.
- This is expensive but ensures the map stays efficient.
- Analogy: If the library runs out of shelf space, it doubles the number of shelves and reorganizes all books.

## ➡️ 5. Difference between HashMap and ConcurrentHashMap.

### 🟦 Thread-Safety

- **HashMap:**
  - Not thread-safe. If multiple threads modify it simultaneously without synchronization, it can lead to inconsistencies like infinite loops (pre-Java 8) or data corruption.
  - For thread-safety, wrap it with Collections.synchronizedMap(new HashMap<>()), but this locks the entire map, reducing concurrency.
- **ConcurrentHashMap:**
  - Thread-safe and designed for high-concurrency scenarios.
  - It allows multiple threads to read and write without external **synchronization**, using techniques like **lock striping** (**segmented locking**) in **Java 7** or **CAS (Compare-And-Swap)** in **Java 8+** for better performance.

### 🟦 Performance

- **HashMap:** Faster in single-threaded environments due to no overhead for concurrency.
- **ConcurrentHashMap:** Slightly slower in single-threaded but excels in multi-threaded apps (e.g., web servers). It supports full concurrency for reads and adjustable concurrency for writes (default 16 segments).

### 🟦 Null Handling

- **HashMap:** Allows one null key and multiple null values.
- **ConcurrentHashMap:** Does not allow null keys or values (throws NullPointerException).

### 🟦 Iteration

- **HashMap:** Fail-fast iterators; concurrent modification throws ConcurrentModificationException.
- **ConcurrentHashMap:** Weakly consistent iterators; allows modifications during iteration without exceptions, but may not reflect all changes.

### 🟦 Use Cases

- **HashMap:** Single-threaded apps or when synchronization is handled externally.
- **ConcurrentHashMap:** Multi-threaded environments like caches in Spring or shared data in servers.

### 🟦 Other Differences

- `ConcurrentHashMap` provides atomic operations like `putIfAbsent`, `computeIfAbsent`.
- In **Java 8+**, both support functional-style operations, but `ConcurrentHashMap` ensures thread-safety in them.

## ➡️ 6. What are checked and unchecked exceptions? Give examples.

### 🟦 Checked Exception (Compile-time exception):

- These are exceptions that the compiler forces you to handle (using **try-catch** or **throws** keyword).
- They represent **recoverable conditions(recoverable issues)** that the program should anticipate and handle gracefully. Checked exceptions force robust error handling (Use checked exceptions for external failures like **files**, **DB**).
- They extend the `Exception` class but not `RuntimeException`. external failures

- **Example:** `IOException`, `SQLException`, `ClassNotFoundException`, `FileNotFoundException`

### 🟦 Unchecked Exception (Runtime exception):

- The compiler does not force handling them.
- They usually indicate **programming errors** (like **null access**, **invalid index**, etc.).
- Unchecked exceptions indicate **bugs in logic** (should be avoided with **validations**).
- **Example:** `NullPointerException`, `ArrayIndexOutOfBoundsException`, `ArithmeticException`.

## ➡️ 7. Explain Garbage Collection (GC) in Java and different GC algorithms.

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

## ➡️ 10. How does Java memory model (JVM memory areas: heap, stack, metaspace) work?

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
