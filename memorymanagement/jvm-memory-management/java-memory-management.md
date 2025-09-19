🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Java Memory Model

The Java Memory Model is how the Java Virtual Machine (JVM) organizes and manages memory to run a Java program. Think of the JVM as a warehouse where your program’s data is stored and processed.

- The warehouse is divided into different sections, each with a specific purpose: the Heap, Stack, and Metaspace.

### 🔵 Heap

- This is the main storage area where all objects (like strings, arrays, or instances of classes) are stored.
- Analogy: Think of the Heap as a big storage room where you keep all the "things" your program creates, like boxes of data (objects).
- It’s shared across all threads in a program, meaning all parts of your program can access objects in the Heap.
  The Heap is further divided into:
  - Young Generation: Where new objects are created. It’s like a "temporary storage" area for new boxes. It has smaller sections called Eden and Survivor Spaces.
  - Old Generation: Where long-lived objects are moved. It’s like a "permanent storage" area for boxes you keep using.
- The Heap is managed by the Garbage Collector, which cleans up unused objects to free up space.

### 🔵 Stack

- This is where method calls and local variables (like int x = 5) are stored.
- **Analogy:** Think of the Stack as a stack of notepads, one for each method call. When you call a method, you add a new notepad (called a stack frame) to write its variables and track its execution. When the method finishes, you throw away that notepad.
- Each thread in a Java program has its own Stack, so threads don’t interfere with each other’s method calls.
- The Stack is very fast because it’s small and structured (**LIFO: Last In, First Out**).

### 🔵 Metaspace

- This is where class metadata is stored, like the blueprints of your classes (e.g., class definitions, method information).
- **Analogy:** Think of Metaspace as a filing cabinet where the JVM keeps instructions on how to build and use your objects.
- Before **Java 8**, this was called PermGen (Permanent Generation), but Metaspace is more flexible and grows dynamically, reducing the chance of running out of space.
- It’s not part of the Heap and is managed separately.
