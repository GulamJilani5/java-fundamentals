⏺️ ➡️ 🟦 🔵🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Java 17

### ➡️ Sealed Classes (Finalized):🟠

- Sealed classes were introduced in **Java 15 (as a preview)** and made stable in **Java 17**.
- A sealed class or interface in Java allows you to control which classes can extend or implement it.
- It provides a middle ground between:
  - final classes → no one can extend
  - normal classes → anyone can extend

#### 🟦 Key Points

- Declared with sealed keyword.
- Must specify permitted subclasses with permits.
- Subclasses must be either:
  - final → cannot be extended further
  - sealed → can further restrict who can extend
  - non-sealed → removes restrictions and allows anyone to extend further

- Helps in exhaustive pattern matching in switch expressions.
- Encourages well-defined hierarchies, especially in domain models.

##### How to explain in interview

"In Java, a sealed class restricts which other classes can extend or implement it. For example, if I have a Shape class, I can seal it and permit only Circle, Rectangle, and Triangle to extend it. This gives me more control over my class hierarchy and helps avoid unwanted subclasses. Each permitted subclass must declare whether it’s final, sealed, or non-sealed. This is very useful when you want to design APIs or domain models with strict inheritance rules.”

#### 🟦 Modifiers

| Modifier     | Description                                     |
| ------------ | ----------------------------------------------- |
| `sealed`     | Restricts inheritance to a fixed set of classes |
| `final`      | Can not be inherited                            |
| `non-sealed` | Lifts restrictions, allowing anyone to extend   |

#### 🟦 Sealed class Syntax

```java
sealed class Vehicle permits Car, Bike {
}

```

- Allowed subclasses:

```java
final class Car extends Vehicle {
}

non-sealed class Bike extends Vehicle {
}

```

### 🟦 Sealed interface Syntax

```java
sealed interface Payment permits UPI, Card {
}

```

- Implementations:

```java
final class UPI implements Payment {
}

non-sealed class Card implements Payment {
}

```

### ➡️ Pattern Matching for instanceof (Finalized):🟠

```java
 if(obj instance String s){
    System.out.println(s.length);
 }
```

### ➡️ Record Class 🟠 || Production ready

#### 🟦 Record Features (Automatically Generated)

- Constructor
- Getters (called as methods: id(), name() etc)
- toString()
- equals() and hashCode()
- Immutable fields (final by default)

```java
import java.time.LocalDate;

public record Employee(long id, String name, LocalDate joiningDate, double salary) {

    public static void main(String[] args) {

        Employee emp1 = new Employee(101, "Gulam Jilani", LocalDate.of(2024, 5, 10), 75000.50);

        System.out.println(emp1);

        System.out.println("ID: " + emp1.id());
        System.out.println("Name: " + emp1.name());
        System.out.println("Joining Date: " + emp1.joiningDate());
        System.out.println("Salary: " + emp1.salary());
    }
}

```

### ➡️ Shenandoah Garbage Collector (Production-Ready):🟠

- ZGC garbage collection (15-20% faster in prod).

### ➡️ Switch Expression Enhanced

### ➡️ Vector API (Second Incubator):

### ➡️ Foreign Function & Memory API (Incubator):

### ➡️ Restore Always-Strict Floating-Point Semantics:

### ➡️ Deprecate AOT and JIT Compilation:

### ➡️ New macOS Rendering Pipeline:
