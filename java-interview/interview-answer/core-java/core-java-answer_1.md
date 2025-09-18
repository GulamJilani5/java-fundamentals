🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Answers

## ➡️ 1. == vs equals in java

| **Aspect**      | **`==`**                  | **`.equals()`**                        |
| --------------- | ------------------------- | -------------------------------------- |
| **Works on**    | Primitives & Objects      | Objects only                           |
| **For Objects** | Compares memory addresses | Compares contents (if overridden and ) |
| **Default**     | Reference equality        | Reference equality (unless overridden) |
| **Override?**   | Cannot override           | Can override in a class                |

- **.equals()** is overridden in `value-based classes` where logical equality is more useful than reference equality.
- **Common ones that overrides .equals():** String, all wrapper classes of Primitives, collections, enums.
- In your own classes, you override it if you want two different objects with the same field values to be considered "equal".

## ➡️ 11. log.info("Hello: {}", name); VS log.info("Hello: "+ name);

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
