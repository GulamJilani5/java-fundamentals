⏺️ ➡️ 🟦 🔵🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# Intermediate Operations

- They always return a Stream (or a specialized stream).

  - `Stream<T>`: Same type as input elements
  - `Stream<R>`: Different (transformed) type

| Operation  | Return Type |
| ---------- | ----------- |
| `map`      | `Stream<R>` |
| `flatMap`  | `Stream<R>` |
| `filter`   | `Stream<T>` |
| `sorted`   | `Stream<T>` |
| `distinct` | `Stream<T>` |
| `limit`    | `Stream<T>` |
| `skip`     | `Stream<T>` |
| `peek`     | `Stream<T>` |

- Intermediate operations are lazy in nature.
- They will only execute if there is any terminal operation.
- They do not execute until a terminal operation (forEach, collect, reduce, etc.) is called.
- **Sample Object (Employee)**

```java
  class Employee {
    private int id;
    private String name;
    private String department;
    private double salary;
    private List<String> skills;

    // constructor + getters
}

```

- **Sample Emplyoee Data**

```java
  List<Employee> employees = List.of(
    new Employee(1, "A", "IT", 60000, List.of("Java", "Spring")),
    new Employee(2, "B", "HR", 45000, List.of("Recruitment")),
    new Employee(3, "C", "IT", 70000, List.of("Java", "AWS")),
    new Employee(4, "D", "Sales", 50000, List.of("Negotiation")),
    new Employee(5, "E", "IT", 60000, List.of("Java", "Spring"))
);

```

### ➡️`map(Function)`

- Exactly 1 argument only
- Transforms each element by applying a function, producing a new stream of transformed values.
- **One-to-one mapping:** Each input produces exactly one output.
- **Type-safe:** Can change the stream's element type (e.g., `Integer` to `String`).

- **mapping each elements and collecting in the list**

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> squared = numbers.stream()
        .map(n -> n * n)  // Square each number
        .collect(Collectors.toList());
    System.out.println(squared);  // Output: [9, 1, 16, 1, 25, 81, 4, 36]
```

- Use **forEach** to Print Each Squared Number on a New Line

```java
import java.util.*;
numbers.stream()
    .map(n -> n * n)
    .forEach(System.out::println);
```

- **Object → field**

```java
  employees.stream()
         .map(Employee::getName)
         .forEach(System.out::println);

```

### ➡️`flatMap(Function)`

- Exactly 1 argument only.
- Applies a function that returns a stream for each element, then flattens all resulting streams into a single stream.
- Handles nested structures (e.g., lists of lists) by "flattening" them.
- **One-to-many mapping:** Unlike **map**, it can produce multiple outputs per input.

```java
    List<List<Integer>> nested = Arrays.asList(
        Arrays.asList(1, 2),
        Arrays.asList(3, 4),
        Arrays.asList(5)
    );

    List<Integer> flattened = nested.stream()
        .flatMap(list -> list.stream())  // Flatten into single stream
        .collect(Collectors.toList());
    System.out.println(flattened);  // Output: [1, 2, 3, 4, 5]
```

### ➡️`filter(Predicate)`

- Exactly 1 argument only.
- Filters elements based on a condition, retaining only those that return true from the provided Predicate.
- **Short-circuit friendly:** Can stop early if combined with limit or similar.
- Useful for data filtering without modifying the source.

- **filtering based on certian condition(eg. even numbers)**

```java
    import java.util.*;
    import java.util.stream.Collectors;

    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> evenNumbers = numbers.stream()
        .filter(n -> n % 2 == 0)  // Keep only even numbers
        .collect(Collectors.toList());
    System.out.println(evenNumbers);  // Output: [4, 2, 6]
```

- **Object Filtering**

```java
  employees.stream()
         .filter(e -> e.getSalary() > 50000)
         .forEach(System.out::println);
```

### ➡️`sorted()`

- Sorts elements in their natural order (e.g., ascending for numbers, lexicographical for strings).
- Requires comparable elements or will throw an exception.
- Lazy and efficient for avoiding nested streams.

##### 🟦 No arguments (natural order)

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> sortedAsc = numbers.stream()
        .sorted()  // Natural ascending order
        .collect(Collectors.toList());
    System.out.println(sortedAsc);  // Output: [1, 1, 2, 3, 4, 5, 6, 9]
```

##### 🟦 One argument (Comparator)

- `sorted(Comparator)`

- Sorts elements using a custom Comparator for defining the order.
- Flexible: Allows descending order, custom logic (e.g., by length for strings).
- Stable if the comparator is consistent.
- Lazy, like `sorted()`.

```java
import java.util.Comparator;

List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> sortedDesc = numbers.stream()
    .sorted(Comparator.reverseOrder())  // Custom descending comparator
    .collect(Collectors.toList());
System.out.println(sortedDesc);  // Output: [9, 6, 5, 4, 3, 2, 1, 1]
```

- **Object Example (by salary ascending(default))**

```java
  employees.stream()
         .sorted(Comparator.comparing(Employee::getSalary))
         .forEach(e -> System.out.println(e.getName()));
```

- **Object Example (by salary descending)**

```java
  employees.stream()
         .sorted(Comparator.comparing(Employee::getSalary).reversed())
         .forEach(e -> System.out.println(e.getName()));
```

### ➡️`distinct()`

- no arguments.
- Removes duplicate elements, keeping only unique values based on `equals().`
- Uses hash-based uniqueness: Efficient for large streams but requires good `hashCode/equals`.
- **Order-preserving:** Maintains encounter order.

- **Primitive Example**

```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> unique = numbers.stream()
    .distinct()  // Remove duplicates
    .collect(Collectors.toList());
System.out.println(unique);  // Output: [3, 1, 4, 5, 9, 2, 6]
```

- **Object Example (requires equals & hashCode)**

```java
  employees.stream()
         .distinct()
         .forEach(System.out::println);
```

### ➡️`limit(n)`

- 1 argument only.
- Truncates the stream to the first n elements.
- Short-circuiting: Stops processing after n elements, optimizing performance.
- Useful for pagination or sampling.

- **Stream Example**

```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> firstThree = numbers.stream()
    .limit(3)  // Take first 3 elements
    .collect(Collectors.toList());
System.out.println(firstThree);  // Output: [3, 1, 4]
```

- **Object example**

```java
employees.stream()
         .limit(3)
         .forEach(e -> System.out.println(e.getName()));
```

### ➡️`skip(n)`

- - 1 argument only.
- Discards the first n elements, returning the rest of the stream.
- Short-circuiting: Skips upfront, but processes the remainder lazily.
- Complements limit for pagination (e.g., offset-based).
- No-op if stream has fewer than n elements.

- **Primitive example**

```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> afterFirstTwo = numbers.stream()
    .skip(2)  // Skip first 2 elements
    .collect(Collectors.toList());
System.out.println(afterFirstTwo);  // Output: [4, 1, 5, 9, 2, 6]
```

- **Object example**

```java
employees.stream()
         .skip(2)
         .forEach(e -> System.out.println(e.getName()));

```

### ➡️`peek(Consumer)`

- 1 argument only.
- For Inspect / Debug.
- Performs an action (e.g., printing) on each element without modifying the stream.
- Non-interfering: Doesn't alter elements; purely for side effects like debugging or logging.
- Useful for inspecting intermediate results without breaking the pipeline.

- **Primitive example**

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> doubled = numbers.stream()
        .peek(n -> System.out.print(n + " "))  // Debug: print each before doubling
        .map(n -> n * 2)
        .collect(Collectors.toList());
    // Console output during execution: 3 1 4 1 5 9 2 6
    System.out.println(doubled);  // Output: [6, 2, 8, 2, 10, 18, 4, 12]
```

- **Object example**

```java
    employees.stream()
         .peek(e -> System.out.println("Before filter: " + e.getName()))
         .filter(e -> e.getSalary() > 50000)
         .peek(e -> System.out.println("After filter: " + e.getName()))
         .forEach(e -> System.out.println(e.getName()));

```
