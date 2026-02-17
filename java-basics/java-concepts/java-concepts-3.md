⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ equals() and hashCode()

```java
import java.util.HashSet;
import java.util.Objects;
import java.util.Set;

class Employee {
    long id;
    String name;

    Employee(long id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Employee)) return false;
        Employee that = ()Employee) o;
        return this.id == that.id;
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);
    }
}

public class Main {
    public static void main(String[] args) {

        Employee e1 = new Employee(1, "Ali");
        Employee e2 = new Employee(1, "Ali");

        System.out.println(e1.equals(e2)); // true

        Set<Employee> set = new HashSet<>();
        set.add(e1);
        set.add(e2);

        System.out.println(set.size()); // 1 (Duplicate removed!)
    }
}

```

### ➡️ equals()

#### 🟦 if (this == o) return true;

- Same reference then it will return true

#### 🟦 if (!(o instanceof Employee)) return false;

- **o == null**
  - then return false
- **O is not an Employee object**
  - then return false
- **o is type of Employee**
  - then go to casting and comparing id

#### 🟦 Casting and returning true/false

```java
Employee that = ()Employee) o; // Casting to Employee Object
return this.id == that.id;  // Comparing ids
```

- **If both ids are same**
  - return `true`
- **If both ids are different**
  - return `false`
