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
