## ➡️ 1. What are checked and unchecked exceptions? Give examples.

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

🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ 12. stacoverflow error vs outOfMemoryError

### 🟦 StackOverflowError

- Every program has a stack in memory → it’s used to keep track of method calls.
- Imagine the stack like a pile of plates. Every time a method is called, a new plate is added. When the method finishes, the plate is removed.

- **Normal Case:** add a few plates, remove them → stack works fine.
- **StackOverflowError:** you keep adding plates forever without removing them → the stack overflows.

##### 🔵 Common Cause:

- A function calls itself again and again without a proper exit condition (infinite recursion).
- This will quickly fill the stack → StackOverflowError.

```java
public void recurse() {
    recurse(); // calls itself forever
}

```

### 🟦 OutOfMemoryError

- Java programs also have a big memory area called the heap → used to store objects (e.g., strings, arrays, classes).
- If your program tries to create more objects than the heap can hold, Java says “OutOfMemoryError”.

- **Normal Case:** you create objects, and garbage collector cleans up unused ones.
- **OutOfMemoryError:** too many objects stay in memory or one object is too big, so Java runs out of

##### 🔵 Common Cause:

- Creating a very large object (like a giant array).
- Memory leak → holding references to objects you no longer need.
- Heap keeps filling → OutOfMemoryError.

```java
List<String> list = new ArrayList<>();
while(true){
    list.add("Hello"); // keeps adding strings forever
}
```
