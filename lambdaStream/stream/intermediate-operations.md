🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# Intermediate Operations

- Intermediate operations are lazy in nature.
- They will only execute if there is any terminal operation.

### ➡️`map(Function)`

- Transforms each element by applying a function, producing a new stream of transformed values.
- **One-to-one mapping:** Each input produces exactly one output.
- **Type-safe:** Can change the stream's element type (e.g., `Integer` to `String`).
- Lazy: Applies transformation only when needed.

- **way 1**

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> squared = numbers.stream()
        .map(n -> n * n)  // Square each number
        .collect(Collectors.toList());
    System.out.println(squared);  // Output: [9, 1, 16, 1, 25, 81, 4, 36]
```

- **way 2**
  - Use **forEach** to Print Each Squared Number on a New Line

```java
import java.util.*;

numbers.stream()
    .map(n -> n * n)
    .forEach(System.out::println);  // Output:
                                    // 9
                                    // 1
                                    // 16
                                    // 1
                                    // 25
                                    // 81
                                    // 4
                                    // 36
```

- **way 3**
  - Use **forEach** with Custom Formatting (**e.g.**, "Squared: X")

```java
import java.util.*;

numbers.stream()
    .map(n -> n * n)
    .forEach(n -> System.out.println("Squared: " + n));  // Output:
                                                         // Squared: 9
                                                         // Squared: 1
                                                         // Squared: 16
                                                         // Squared: 1
                                                         // Squared: 25
                                                         // Squared: 81
                                                         // Squared: 4
                                                         // Squared: 36
```

### ➡️`flatMap(Function)`

- Applies a function that returns a stream for each element, then flattens all resulting streams into a single stream.
- Handles nested structures (e.g., lists of lists) by "flattening" them.
- **One-to-many mapping:** Unlike **map**, it can produce multiple outputs per input.
- Lazy and efficient for avoiding nested streams.

```java
    List<List<Integer>> nested = Arrays.asList(
        Arrays.asList(1, 2), Arrays.asList(3, 4), Arrays.asList(5)
    );
    List<Integer> flattened = nested.stream()
        .flatMap(list -> list.stream())  // Flatten into single stream
        .collect(Collectors.toList());
    System.out.println(flattened);  // Output: [1, 2, 3, 4, 5]
```

### ➡️`filter(Predicate)`

- Filters elements based on a condition, retaining only those that return true from the provided Predicate.
- **Short-circuit friendly:** Can stop early if combined with limit or similar.
- Useful for data filtering without modifying the source.
- Lazy: Only evaluates elements as needed by downstream operations.

```java
    import java.util.*;
    import java.util.stream.Collectors;

    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> evenNumbers = numbers.stream()
        .filter(n -> n % 2 == 0)  // Keep only even numbers
        .collect(Collectors.toList());
    System.out.println(evenNumbers);  // Output: [4, 2, 6]
```

### ➡️`sorted()`

- Sorts elements in their natural order (e.g., ascending for numbers, lexicographical for strings).
- Requires comparable elements or will throw an exception.
- Lazy and efficient for avoiding nested streams.

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> sortedAsc = numbers.stream()
        .sorted()  // Natural ascending order
        .collect(Collectors.toList());
    System.out.println(sortedAsc);  // Output: [1, 1, 2, 3, 4, 5, 6, 9]
```

### ➡️`sorted(Comparator)`

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

### ➡️`distinct()`

- Removes duplicate elements, keeping only unique values based on `equals().`
- Uses hash-based uniqueness: Efficient for large streams but requires good hashCode/equals.
- Lazy: Deduplication deferred until terminal operation.
- **Order-preserving:** Maintains encounter order.

```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> unique = numbers.stream()
    .distinct()  // Remove duplicates
    .collect(Collectors.toList());
System.out.println(unique);  // Output: [3, 1, 4, 5, 9, 2, 6]
```

### ➡️`limit(n)`

- Truncates the stream to the first n elements.
- Short-circuiting: Stops processing after n elements, optimizing performance.
- Lazy: Only advances the source stream as needed.
- Useful for pagination or sampling.

```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> firstThree = numbers.stream()
    .limit(3)  // Take first 3 elements
    .collect(Collectors.toList());
System.out.println(firstThree);  // Output: [3, 1, 4]
```

### ➡️`skip(n)`

- Discards the first n elements, returning the rest of the stream.
- Short-circuiting: Skips upfront, but processes the remainder lazily.
- Complements limit for pagination (e.g., offset-based).
- No-op if stream has fewer than n elements.

```java
  List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
List<Integer> afterFirstTwo = numbers.stream()
    .skip(2)  // Skip first 2 elements
    .collect(Collectors.toList());
System.out.println(afterFirstTwo);  // Output: [4, 1, 5, 9, 2, 6]
```

### ➡️`peek(Consumer)`

- Performs an action (e.g., printing) on each element without modifying the stream.
- Non-interfering: Doesn't alter elements; purely for side effects like debugging or logging.
- Lazy: Action runs only during traversal by a terminal operation.
- Useful for inspecting intermediate results without breaking the pipeline.

```java
    List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9, 2, 6);
    List<Integer> doubled = numbers.stream()
        .peek(n -> System.out.print(n + " "))  // Debug: print each before doubling
        .map(n -> n * 2)
        .collect(Collectors.toList());
    // Console output during execution: 3 1 4 1 5 9 2 6
    System.out.println(doubled);  // Output: [6, 2, 8, 2, 10, 18, 4, 12]
```
