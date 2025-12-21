⏺️ ➡️ 🟦 🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Answers

## ➡️ 1. == vs equals in java

| **Aspect**      | **`==`**                  | **`.equals()`**                        |
| --------------- | ------------------------- | -------------------------------------- |
| **Works on**    | Primitives & Objects      | Objects only                           |
| **For Objects** | Compares memory addresses | Compares contents (if overridden and ) |
| **Default**     | Reference equality        | Reference equality (unless overridden) |
| **Override?**   | Cannot override           | Can override in a class                |

- If any class overrides **.equals()** method then it will compare content only otherwise comparing the referencs.
- String, Integer, Double and all wrapper classes of Primitives, collections, enums overrrides **.equals** so they compares by content not reference.
- Our **Custom Class** must override **.equals()** in order to compare by contents not reference.

### 🟦 **hashCode()**

- **hashCode()** is following the exactly same as **.equals()**

## ➡️ Immutable Class

- An immutable class in Java is a class whose objects cannot be modified after creation.
  - Once an object is initialized, its state never changes
  - Any “change” results in a new object, not modification of the existing one

### 🟦 Why Immutable Classes Matter

- Thread-Safe by Design
- Easier to Reason & Debug
- Safe for Hash-Based Collections(`hashCode()` remains consistent)
  - HashMap keys
  - HashSet elements
- Prevents Accidental Data Modification

### 🟦 Classic Examples of Immutable Classes

- String, Integer, Long, LocalDate, LocalDateTime

### 🟦 Rules to Create a Custom Immutable Class

- Declare the Class as final
  - Prevents subclassing
  - Subclasses could add setters or mutable behavior
- Make All Fields private and final
  - **private** → no external modification
  - **final** → assigned only once
- Do NOT Provide Setter Methods
- Initialize Fields Using Constructor Only
- Return Defensive Copies for Mutable Fields

## ➡️ Serialization vs Marker Interface

### 🟦 Serialization

- Serializable is a **Marker Interface** from `java.io` package.
- **Serialization** means converting an object into a byte stream (a series of bytes) so it can be:

  - Saved to a file or database, or
  - Transferred over a network.

- Later, it can be **deserialized** — converted back from the byte stream into the original Java object.

```java
  import java.io.*;

class Employee implements Serializable {
    int id;
    String name;

    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

public class TestSerialization {
    public static void main(String[] args) throws Exception {
        Employee emp = new Employee(101, "Gulam");

        // Serialize (write object to file)
        FileOutputStream fos = new FileOutputStream("emp.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(emp);
        oos.close();

        // Deserialize (read object from file)
        FileInputStream fis = new FileInputStream("emp.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Employee e = (Employee) ois.readObject();
        ois.close();

        System.out.println(e.id + " " + e.name);
    }
}

```

### 🟦 Marker Interface

- A Marker Interface is an interface that has no methods or fields — it’s used to mark a class with metadata that gives special behavior to the JVM or compiler.

  | Marker Interface | Purpose                                                         |
  | ---------------- | --------------------------------------------------------------- |
  | `Serializable`   | Marks that the object can be serialized                         |
  | `Cloneable`      | Marks that object can be cloned using `clone()`                 |
  | `Remote`         | Marks that object can be used in RMI (Remote Method Invocation) |
