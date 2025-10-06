🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ What is record

- Java Records were introduced in **Java 14 (as a preview)** and became a standard feature in **Java 16**.
- A Record is a special kind of class in Java that is **immutable**, **final**, and designed to hold data without the boilerplate code like `constructors`, `getters`, `equals()`, `hashCode()`, and `toString()`.
- There are no **setters** in Java Records because the fields inside a record are final and immutable by design.
- Think of records as a quick way to define **DTOs (Data Transfer Objects)**.

### 🟦 Syntax of a Record

```java
record RecordName(FieldType fieldName, FieldType fieldName2) {
    // optional methods or static blocks
}

```

- **It automatically generates**

  - A canonical constructor (with parameters for all fields)
  - `Getters` (methods with the same name as the fields)
  - `equals()` and `hashCode()`
  - `toString()`

- The fields are **final** and cannot be changed after the object is created
