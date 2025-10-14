🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Optional Class:

- `java.util` package that helps handle situations where a value may or may not be present, reducing the risk of `NullPointerException`.

## ➡️ Methods of Optional Class

### 🟦 Creation

##### 🔵 Optional.of(T value)

- Creates an Optional instance containing the specified non-null value. If the provided value is null, it throws a `NullPointerException (NPE)`.
- Ensures the value is non-null at creation time, preventing null-related issues early.
- Useful when you are certain the value is not null and want to enforce that contract.
- Returns an `Optional` that is present (not empty).

```java
import java.util.Optional;
public class Example {
    public static void main(String[] args) {
        String name = "Alice";  // Non-null value
        Optional<String> optionalName = Optional.of(name);

        // Usage: Check if present and get value
        if (optionalName.isPresent()) {
            System.out.println("Name: " + optionalName.get());  // Output: Name: Alice
        }
    }
}
```

##### 🔵 Optional.ofNullable(T value)

- Creates an Optional instance containing the specified value, or an empty Optional if the value is null.
- Handles potentially null values gracefully without throwing exceptions.
- Allows safe wrapping of values that might be null, promoting null-safety.
- Returns a present Optional if non-null, or empty if null.

```java
   import java.util.Optional;
    public class Example {
        public static void main(String[] args) {
            String name = null;  // Potentially null value
            Optional<String> optionalName = Optional.ofNullable(name);

            // Usage: Handle empty case
            optionalName.ifPresentOrElse(
                value -> System.out.println("Name: " + value),
                () -> System.out.println("Name is null")  // Output: Name is null
            );
        }
    }
```

##### 🔵 Optional.empty()

- Returns an empty `Optional` instance (i.e., an Optional with no value present).
- Provides a standard way to represent the absence of a value explicitly.
- Useful for default cases or when you need to return an empty optional from a method.
- Always returns an empty (absent) `Optional`, which can be chained with operations like `orElse()`.

```java
   import java.util.Optional;

    public class Example {
        public static void main(String[] args) {
            Optional<String> emptyOptional = Optional.empty();

            // Usage: Provide a default value
            String result = emptyOptional.orElse("Default Name");
            System.out.println("Result: " + result);  // Output: Result: Default Name
        }
    }
```

### 🟦 Checking Presence

##### 🔵 boolean isPresent()

- Returns true if there is a value present in the Optional, otherwise false.
- Provides a simple way to check for the existence of a value without accessing it.
- Useful in conditional logic to avoid exceptions when dealing with potentially empty Optionals.
- Does not throw exceptions and is lightweight.

```java
import java.util.Optional;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        if (optionalName.isPresent()) {
            System.out.println("Value is present");  // Output: Value is present
        }
    }
}
```

##### 🔵 boolean isEmpty()

- Returns true if there is no value present in the `Optional`, otherwise false. (Introduced in **Java 11**)
- Complements `isPresent()` by directly checking for emptiness, making code more readable for negation cases.
- Avoids the need for `!isPresent()`, improving clarity in modern Java code.
- Does not throw exceptions and is efficient.

```java
  import java.util.Optional;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.empty();

        if (optionalName.isEmpty()) {
            System.out.println("No value present");  // Output: No value present
        }
    }
}
```

### 🟦 Accessing the Value

##### 🔵 T get()

- Returns value if present, else throws `NoSuchElementException`
- Direct access to the value when you're certain it's present (e.g., after `isPresent()` check).
- Throws an exception for empty cases, enforcing explicit handling of absence.
- Not recommended for unchecked scenarios due to potential runtime errors.

```java
  import java.util.Optional;
    public class Example {
        public static void main(String[] args) {
            Optional<String> optionalName = Optional.of("Alice");

            if (optionalName.isPresent()) {
                String name = optionalName.get();
                System.out.println("Name: " + name);  // Output: Name: Alice
            }
            // Note: Calling get() on empty would throw NoSuchElementException
        }
    }
```

##### 🔵 T orElse(T other)

- Returns the value if present; otherwise returns the specified default value `other`.
- Provides a fallback value without exceptions, making it safe for null-like scenarios.
- The default value is eagerly evaluated (computed immediately, even if not needed).
- Useful for simple defaults in method returns or assignments.

```java
  import java.util.Optional;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.empty();

        String name = optionalName.orElse("Default Name");
        System.out.println("Name: " + name);  // Output: Name: Default Name
    }
}
```

##### 🔵 T orElseGet(Supplier<? extends T> supplier)

- Returns the value if present; otherwise invokes the `Supplier` and returns its result.
- Lazily evaluates the fallback (supplier is called only if empty), improving performance for expensive computations.
- More efficient than `orElse()` when the default is costly to compute.
- Allows dynamic defaults based on context.

```java
  import java.util.Optional;
import java.util.function.Supplier;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.empty();

        String name = optionalName.orElseGet(() -> "Computed Default");
        System.out.println("Name: " + name);  // Output: Name: Computed Default
        // Supplier is only called if empty
    }
}
```

##### 🔵 <T> T orElseThrow()

- Returns the value if present; otherwise throws a `NoSuchElementException.` (Note: The generic <T> in the signature is likely a formatting error; it's T `orElseThrow()`).
- Similar to get(), but without generics in the method name for the return type.
- Enforces handling absence via exceptions, useful in imperative code where failure is expected.
- Throws a standard exception for empty cases.

```java
import java.util.Optional;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        try {
            String name = optionalName.orElseThrow();
            System.out.println("Name: " + name);  // Output: Name: Alice
        } catch (Exception e) {
            System.out.println("Exception: " + e.getMessage());
            // Would print exception message if empty
        }
    }
}
```

##### 🔵 <T> T orElseThrow(Supplier<? extends X> exceptionSupplier)

- Returns the value if present; otherwise throws the exception produced by the `exceptionSupplier`. (Note: The `<T>` is part of the generic return type; `X` is the exception type)
- Allows custom exceptions instead of the default `NoSuchElementException`.
- The supplier enables lazy exception creation, useful for context-specific errors.
- Enhances error handling flexibility in validation or business logic.

```java
    import java.util.Optional;
    import java.util.function.Supplier;
    import java.util.NoSuchElementException;

    public class Example {
        public static void main(String[] args) {
            Optional<String> optionalName = Optional.empty();

            try {
                String name = optionalName.orElseThrow(
                    () -> new IllegalArgumentException("Name cannot be null")
                );
            } catch (IllegalArgumentException e) {
                System.out.println("Custom Exception: " + e.getMessage());
                // Output: Custom Exception: Name cannot be null
            }
        }
    }
```

### 🟦 Conditional Execution

##### 🔵 ifPresent(Consumer<? super T> consumer):

- If a value is present, invokes the specified `consumer` with the value; otherwise does nothing.
- Executes side-effects (**e.g.**, `logging`, `printing`) only if present, avoiding null checks.
- Encourages functional style by passing actions as lambdas.
- No return value; purely for execution.

```java
import java.util.Optional;
import java.util.function.Consumer;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        optionalName.ifPresent(name -> System.out.println("Hello, " + name));
        // Output: Hello, Alice
    }
}
```

##### 🔵 ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction) (Java 9+):

- If a value is present, invokes the action with the value; otherwise invokes the emptyAction. (Introduced in **Java 9**).
- Handles both present and empty cases in one method, reducing branching.
- Supports side-effects for both scenarios, like logging success or absence.
- Improves readability for complete conditional execution.

```java
    import java.util.Optional;
    import java.util.function.Consumer;

    public class Example {
        public static void main(String[] args) {
            Optional<String> optionalName = Optional.empty();

            optionalName.ifPresentOrElse(
                name -> System.out.println("Hello, " + name),
                () -> System.out.println("No name provided")  // Output: No name provided
            );
        }
    }
```

### 🟦 Transforming or Chaining

##### 🔵 map

- If a value is present, applies the mapper function to it and returns an Optional containing the result; otherwise returns an empty Optional.
- Enables functional transformation of values within the Optional chain.
- Returns a new Optional, preserving null-safety without explicit checks.
- Useful for method chaining in stream-like operations.

```java
  import java.util.Optional;
import java.util.function.Function;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        Optional<Integer> length = optionalName.map(String::length);
        length.ifPresent(len -> System.out.println("Length: " + len));  // Output: Length: 5
    }
}
```

##### 🔵 flatMap

- If a value is present, applies the ` mapper` function (which returns an `Optional`) to it and returns the result; otherwise returns an empty `Optional`. Flattens nested Optionals.
- Handles nested Optionals by flattening them, avoiding `Optional<Optional<U>>`.
- Ideal for chaining operations where intermediate results are themselves Optionals (e.g., lookups).
- Promotes composable, monadic-style code.

```java
import java.util.Optional;
import java.util.function.Function;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        Optional<Optional<Integer>> nested = optionalName.map(name -> Optional.of(name.length()));
        Optional<Integer> flattened = optionalName.flatMap(name -> Optional.of(name.length()));

        flattened.ifPresent(len -> System.out.println("Length: " + len));  // Output: Length: 5
    }
}
```

##### 🔵 filter

- If a value is present and the value matches the `predicate`, returns an `Optional` containing the value; otherwise returns an empty `Optional`.
- Allows conditional filtering within the `Optional`, keeping only matching values.
- Non-mutating; returns a new `Optional` for chaining.
- Useful for validation or selective processing without if-statements.

```java
import java.util.Optional;
import java.util.function.Predicate;

public class Example {
    public static void main(String[] args) {
        Optional<String> optionalName = Optional.of("Alice");

        Optional<String> filtered = optionalName.filter(name -> name.length() > 3);
        filtered.ifPresent(name -> System.out.println("Filtered Name: " + name));
        // Output: Filtered Name: Alice
    }
}
```
