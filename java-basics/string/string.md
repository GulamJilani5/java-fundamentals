⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ String Literal vs String Object (Using new Keyword)

### ➡️ String Literal

- Stored in String Constant Pool (SCP).
- Immutable → once created, value cannot change.
- JVM tries to reuse literals → if "Hello" already exists, it returns the same reference.

```java
  String a = "Gulam";
  String b = "Gulam";
```

- "Gulam" already exists in SCP.
- Both a and b point to the same object.
- Saves memory and Faster

##### 🟦 Benefits

- Fast
- Memory-efficient
- Interning happens automatically

### ➡️ String Object (Using new Keyword)

- NOT stored in SCP by default → stored in heap memory.
- Immutable → same immutability as literal.

##### 🟦 `new String()` always puts a new object in heap.

```java
  String c = new String("Hello");
String d = new String("Hello");

```

- **Memory**

```
Heap:
 "Hello"  <-- c
 "Hello"  <-- d

```

- new String() forces a fresh object in heap.
- JVM never tries to reuse heap objects.
- Even though values match, objects are different.

##### 🟦 Benefits

- JVM creates new object intentionally (e.g., security-sensitive operations)
- Used when reading from user input, files, network, etc.
