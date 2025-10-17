🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

⏺️ Java 25

## ➡️ Simplified Hello World (Instance Main Methods)

#### 🟦 Before (Java 24)

```java
  public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

#### 🟦 After (Java 25)

```java
  void main() {
    println("Hello, World!");
}
```

## ➡️ Module Import Declarations (Simplified Imports)

#### 🟦 Before (Java 24)

```java
  import java.util.List;
import java.util.Map;
import java.util.Set;
import java.util.stream.Stream;
import java.util.Collectors;
import java.util.function.Function;
import java.nio.file.Path;
import java.nio.file.Files;

public class DataProcessor {
    // Your code here
}
```

#### 🟦 After (Java 25)

```java
  import module java.base;

public class DataProcessor {
    // All java.base classes available automatically!
    // List, Map, Stream, Path...
}
```

## ➡️ Primitive Pattern Matching (instanceof with Primitives)

#### 🟦 Before (Java 24)

```java
   void test(Object obj) {
    if (obj instanceof Integer) {
        int i = (Integer) obj;
        if (i >= 0 && i <= 127) {
            // Can safely use as byte
            byte b = (byte) i;
            System.out.println(b);
        }
    }
}
```

#### 🟦 After (Java 25)

```java
  void test(Object obj) {
    if (obj instanceof byte b) {
        // Direct check & assignment!
        System.out.println(b);
    }
}
```

## ➡️ Primitive Pattern Matching (switch with Primitives)

#### 🟦 Before (Java 24)

```java
  String grade(Number n) {
    if (n instanceof Integer i) {
        if (i >= 90) return "A";
        if (i >= 75) return "B";
        if (i >= 60) return "C";
    } else if (n instanceof Double d) {
        if (d >= 59.5) return "C";
    }
    return "D/F";
}
```

#### 🟦 After (Java 25)

```java
  String grade(Number n) {
    return switch (n) {
        case int i when i >= 90 -> "A";
        case int i when i >= 75 -> "B";
        case int i when i >= 60 -> "C";
        case double d when d >= 59.5 -> "C (rounded)";
        default -> "D/F";
    };
}
```

## ➡️ Flexible Constructor Bodies (Code Before super())

#### 🟦 Before (Java 24)

```java
  class Employee extends Person {
    Employee(String name, int age) {
        super(name, age);
        // Validation AFTER super
        if (age < 18 || age > 67) {
            throw new IllegalArgumentException("Invalid age");
        }
    }
}
```

#### 🟦 After (Java 25)

```java
  class Employee extends Person {
    Employee(String name, int age) {
        // Validate BEFORE super!
        if (age < 18 || age > 67) {
            throw new IllegalArgumentException("Invalid age");
        }
        super(name, age);
    }
}
```

## ➡️ Structured Concurrency (Preview)

#### 🟦 Before (Java 24)

```java
  ExecutorService executor = Executors.newCachedThreadPool();
Future<String> user = executor.submit(() -> fetchUser());
Future<Order> order = executor.submit(() -> fetchOrder());
String u = user.get();
Order o = order.get();
executor.shutdown();
// Manual error handling needed!
```

#### 🟦 After (Java 25)

```java
  try (var scope = StructuredTaskScope.open()) {
    var user = scope.fork(() -> fetchUser());
    var order = scope.fork(() -> fetchOrder());
    scope.join();
    return new Result(user.get(), order.get());
} // Auto cleanup & cancellation!
```
