🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️
⏺️ Predefined collector methods in the Collectors class

- collect method is a terminal operation that processes the elements of a stream and accumulates them into a final result, such as a `List`, `Set`, `Map`, or a custom data structure.
- Terminal operations, like `collect`, trigger the stream's computation and produce a concrete result, after which the stream cannot be reused.

- common Collector methods from `java.util.stream.Collectors`

## ➡️ Collection Collectors

- These accumulate elements into standard collections.

### 🟦 1. toList()

- Collects all elements into a mutable `ArrayList`. It's the most common way to get a `List` from a stream.
- Duplicates are preserved, and order is maintained.

```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

Stream<String> stream = Stream.of("apple", "banana", "cherry", "date");
List<String> result = stream.collect(Collectors.toList());
System.out.println(result); // Output: [apple, banana, cherry, date]
```

### 🟦 2. toSet()

- Collects unique elements into a mutable `HashSet`. Duplicates are automatically removed, and order is not guaranteed (uses hash-based ordering).

```java
Stream<String> stream = Stream.of("apple", "banana", "apple", "date");  // Note duplicate "apple"
Set<String> result = stream.collect(Collectors.toSet());
System.out.println(result); // Output: [apple, banana, date] (order may vary)
```

### 🟦 3. toUnmodifiableList() (Available since Java 10)

- Collects elements into an immutable `List` (backed by an array). It's like `toList()` but throws `UnsupportedOperationException` on modification attempts, useful for thread-safe or API-returning lists.

```java
Stream<String> stream = Stream.of("apple", "banana", "cherry");
List<String> result = stream.collect(Collectors.toUnmodifiableList());
System.out.println(result);
// result.add("extra");  // Would throw UnsupportedOperationException
// Output: [apple, banana, cherry]
```

## ➡️ Mapping Collectors

- These transform elements into keys/values for structured results.

### 🟦 1. toMap(keyMapper, valueMapper)

- Collects into a HashMap<K, V>, where each element is mapped to a key (via keyMapper) and value (via valueMapper).
- Keys must be unique; if duplicates occur, you can provide a merge function as a third parameter (**e.g.**, `toMap(keyMapper, valueMapper, (existing, replacement) -> replacement)`).
- Throws `IllegalStateException` on key collisions without a merger.

```java
 Stream<String> stream = Stream.of("apple", "banana", "cherry");
Map<Integer, String> result = stream.collect(Collectors.toMap(
    s -> s.length(),  // keyMapper: string length
    s -> s            // valueMapper: the string itself
));
System.out.println(result);

// Output: {5=apple, 6=banana, 6=cherry} (Note: for duplicate keys like 6, you'd need a merger; this example //
// assumes unique keys for simplicity)
```

## ➡️ String Manipulation Collectors

- For concatenating or joining text.

### 🟦 1. joining(CharSequence delimiter) (or joining(delimiter, prefix, suffix))

- Concatenates string elements into a single **String**, separated by a delimiter.
- **Optional** prefix/suffix can wrap the result. Non-string streams require a map to strings first.

```java
    Stream<String> stream = Stream.of("apple", "banana", "cherry");
    String result = stream.collect(Collectors.joining(", "));
    System.out.println(result);
    // Output: apple, banana, cherry
```

## ➡️ Reduction Collectors (Numeric)

- These perform aggregations like sums or averages on numeric values (often after mapping to primitives).

### 🟦 1. summingInt(ToIntFunction<? super T> mapper)

- **Maps** each element to an int (via mapper) and returns the sum as an `Integer`.
- Useful for totaling numeric properties; handles overflow by wrapping around.

```java
    Stream<String> stream = Stream.of("1", "2", "3");
    Integer result = stream.collect(Collectors.summingInt(Integer::parseInt));
    System.out.println(result);
    // Output: 6
```

### 🟦 2. counting()

- Returns the total number of elements in the stream as a `Long`. It's a simple reducer; no mapper needed.

```java
    Stream<String> stream = Stream.of("apple", "banana", "cherry", "date");
    Long result = stream.collect(Collectors.counting());
    System.out.println(result);
    // Output: 4
```

### 🟦 3. averagingInt(ToIntFunction<? super T> mapper)

- `Maps` each element to an int and returns the arithmetic mean as a Double. Returns `NaN` for empty streams.

```java
    Stream<String> stream = Stream.of("1", "2", "3", "4");
    Double result = stream.collect(Collectors.averagingInt(Integer::parseInt));
    System.out.println(result);
    // Output: 2.5
```

## ➡️ Grouping and Partitioning Collectors

- These organize elements into maps based on criteria.

### 🟦 1. groupingBy(Function<? super T, ? extends K> classifier) (or with downstream collector, e.g., groupingBy(classifier, toList()))

- Groups elements by a key produced by classifier, resulting in a Map<K, List<T>> (or custom downstream like `toSet()`). Handles multiple levels with nested collectors.
- Think of `groupingBy` like sorting items into buckets based on a rule.
- We have some fruits, and we want to group them by their length.

```java
    Stream<String> stream = Stream.of("apple", "banana", "cherry", "date");
    Map<Integer, List<String>> result = stream.collect(Collectors.groupingBy(String::length));
    System.out.println(result);
    // Output: {4=[date], 5=[apple], 6=[banana, cherry]}

```

### 🟦 2. partitioningBy(Predicate<? super T> predicate) (or with downstream)

- Partitions elements into a `Map<Boolean, List<T>>` based on a boolean predicate (true/false keys). It's a special case of grouping for binary splits; can include downstream collectors for sub-aggregations.
- `partitioningBy` is just like grouping, but only two buckets:
  - one for elements where the rule is true
  - one for elements where the rule is false
- Split fruits into those longer than 5 letters vs not

```java
 Stream<String> stream = Stream.of("apple", "banana", "cherry", "date");

Map<Boolean, List<String>> result =
        stream.collect(Collectors.partitioningBy(s -> s.length() > 5));
System.out.println(result);
// {false=[apple, date], true=[banana, cherry]}

```
