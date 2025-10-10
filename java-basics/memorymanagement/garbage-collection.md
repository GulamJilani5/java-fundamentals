⏺🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Garbage Collection (GC) in Java and different GC algorithms

- **Garbage Collection (GC)** is Java’s way of automatically cleaning up memory in the **Heap** by removing objects that are no longer needed.
- This prevents memory leaks (where unused objects pile up and consume memory) and makes programming easier because you don’t have to manually free memory like in **C** or **C++**.

### ➡️ What is Garbage Collection?

- When you create an object (e.g., Person p = new Person()), it’s stored in the Heap. If you later set p = null or the object is no longer referenced, it becomes "garbage" because the program can’t access it anymore.
- The Garbage Collector is like a cleaner that periodically scans the Heap, identifies these unused objects, and removes them to free up memory.
- **Analogy:** Imagine a restaurant where plates (objects) are used by customers (your program). When customers leave and no one needs the plates, the cleaner (GC) collects them to make space for new plates.

### ➡️ How Does GC Work?

- **Marking:** The GC identifies which objects are still in use by following references from the program (e.g., variables, collections). Objects with no references are marked as garbage.
- **Sweeping:** The GC removes the marked objects, freeing up memory.
- **Compacting (optional):** The GC may move remaining objects together to make memory allocation more efficient and reduce fragmentation.

### ➡️ Different Garbage Collection Algorithms

##### 🟦 Serial GC:

- Uses a single thread to perform garbage collection.
- Best for small applications or single-core systems.
- Causes longer pauses because it stops the application (called a "stop-the-world" event) to collect garbage.
- **Analogy:** A single cleaner tidying up the entire restaurant alone, pausing all service.

##### 🟦 Parallel GC (Throughput Collector):

- Uses multiple threads to perform garbage collection, making it faster.
- Optimized for throughput (how much work the application can do).
- Still causes stop-the-world pauses but is faster than Serial GC due to parallelism.
- Default in Java 8 for many systems.
- **Analogy:** A team of cleaners working together to tidy up faster, but still pausing service.

##### 🟦 G1 (Garbage-First) GC:

- Divides the Heap into small regions and prioritizes collecting regions with the most garbage (hence "Garbage-First").
- Balances throughput and low latency (shorter pauses).
- Designed for large heaps (e.g., applications with lots of memory).
- Default in Java 9 and later.
- **Analogy:** Cleaning only the messiest tables first to keep the restaurant running smoothly.

##### 🟦 ZGC (Z Garbage Collector):

- A low-latency collector for large-scale applications.
- Keeps pauses very short (often under 10ms), even for huge heaps.
- Ideal for applications needing minimal delays, like real-time systems.
- **Analogy:** A super-efficient cleaner who tidies up without customers noticing.

##### 🟦 Shenandoah GC:

- Similar to ZGC, focuses on low-latency with minimal pauses.
- Works concurrently with the application, reducing stop-the-world events.
- Good for large, responsive applications.
- **Analogy:** A cleaner who tidies up while customers are still eating, causing minimal disruption.
