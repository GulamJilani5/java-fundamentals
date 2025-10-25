✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ ••‣⁎⁕⁜※⁂

## ➡️ No-Argument Constructor (also called the default constructor).

### Why is it important?

- It ensures that an object can be created without explicitly passing any parameters.
- Frameworks like **Hibernate**, **Spring**, and **Jackson** rely on it heavily for object instantiation via reflection.
- If you define any constructor with parameters, **Java** won’t automatically provide a no-args one — you must define it manually.
- It’s especially useful in **serialization/deserialization**, **ORM** mapping, and dependency injection.

```java
    class Employee {
    private String name;
    private int id;

    // No-args constructor
    public Employee() {
    System.out.println("No-Args Constructor Called");
    this.name = "Unknown";
    this.id = 0;
    }

    // Parameterized constructor
    public Employee(String name, int id) {
    this.name = name;
    this.id = id;
    }

    void display() {
    System.out.println("Employee: " + name + ", ID: " + id);
    }

    }
```
