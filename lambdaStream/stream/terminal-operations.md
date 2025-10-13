🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# Terminal Operations

- Terminal operations in Java Streams are methods that produce a result or side effect from the stream pipeline, triggering the computation and closing the stream.
- 🔴 They don't return another stream, making them the end of the chain. Terminal operations cannot be chained.
- Examples are based on this number list.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```

### ➡️`forEach(Consumer)`

- Applies a given action (consumer) to each element in the stream.
- Primarily used for side effects, like printing or updating external state (not for transforming data).
- Order is preserved for sequential streams; no guarantee for parallel streams.
- Returns void, so it's purely for iteration without producing a result.

```java
numbers.stream().forEach(n -> System.out.print(n + " "));
/* Output: 1 2 3 4 5 */
```

### ➡️`collect(Collector)`

- Accumulates stream elements into a mutable result container (e.g., List, Set, Map).
- Highly flexible with built-in collectors like `toList()`, `toSet()`, `joining()`, or custom ones via `Collector.of()`.
- Supports parallelization well for associative operations.
- Returns the collected result (e.g., a Collection).

```java
List<Integer> evenNumbers = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
/* Result: [2, 4] */
```

### ➡️`reduce(...)`

- Combines elements using an accumulator function to produce a single output value (e.g., sum, product, concatenation).
- Overloads: binary operator only (assumes identity like 0 for sum), or with identity and combiner for parallel streams.
- Optional return type if no identity is provided, as the stream might be empty.
- Works best with associative operations for parallelism.

```java
 Optional<Integer> sum = numbers.stream().reduce((a, b) -> a + b);
/* Result: Optional[15] (1+2+3+4+5) */
```

### ➡️`toArray()`

- Converts the stream to an array of the appropriate type.
- Overloads: no-arg (uses runtime type via IntFunction), or with a generator for custom array allocation.
- Useful for interop with legacy array-based APIs.
- Preserves order; supports primitive arrays via specialized streams (e.g., IntStream.toArray()).

```java
Integer[] array = numbers.stream().toArray(Integer[]::new);
/* Result: [1, 2, 3, 4, 5] */
```

### ➡️`count()`

- Returns the number of elements in the stream as a long.
- Short-circuits if possible but typically traverses the entire stream.
- Efficient for sized sources (e.g., Lists); no side effects.
- Commonly used with filter() to count matches.

```java
 long count = numbers.stream().count();
/* Result: 5 */
```

### ➡️`anyMatch(Predicate)`

- Returns true if at least one element matches the predicate; short-circuits on first match.
- Ideal for existence checks without full traversal.
- Works well with parallel streams for early termination.
- Returns boolean; throws exception if predicate is null.

```java
 boolean hasEven = numbers.stream().anyMatch(n -> n % 2 == 0);
/* Result: true */
```

### ➡️`allMatch(Predicate)`

- Returns true if every element matches the predicate; short-circuits on first non-match.
- Efficient for validation (e.g., all positive?).
- Parallel-friendly; returns boolean.
- If stream is empty, returns true by default.

```java
 boolean allPositive = numbers.stream().allMatch(n -> n > 0);
/* Result: true */
```

### ➡️`noneMatch(Predicate)`

- Returns true if no elements match the predicate; short-circuits on first match (opposite of anyMatch).
- Useful for "absence" checks (e.g., none are negative?).
- Returns boolean; empty stream returns true.
- Complements allMatch for full coverage.

```java
  boolean noneNegative = numbers.stream().noneMatch(n -> n < 0);
/* Result: true */
```

### ➡️`findFirst()`

- Returns an Optional with the first element (or empty if none).
- Respects encounter order; short-circuits immediately.
- Preferred for ordered streams; use with limit(1) for unordered.
- Non-deterministic in parallel mode without order.

```java
 Optional<Integer> first = numbers.stream().findFirst();
/* Result: Optional[1] */
```

### ➡️`findAny()`

- Returns an Optional with any element matching the stream (often first in sequential, arbitrary in parallel).
- Short-circuits on first find; faster for parallel streams.
- Useful when order doesn't matter (e.g., existence in large datasets).
- Returns empty if stream is empty.

```java
 Optional<Integer> anyEven = numbers.stream()
    .filter(n -> n % 2 == 0)
    .findAny();
/* Result: Optional[2] (or another even number in parallel) */
```

### ➡️`min(Comparator)`

Returns an Optional with the minimum element based on the comparator.
Traverses the entire stream unless short-circuited (no built-in short-circuit).
Comparator must be consistent; supports custom ordering.
Empty stream returns empty Optional.

```java
 Optional<Integer> min = numbers.stream().min(Integer::compareTo);
/* Result: Optional[1] */
```

### ➡️`max(Comparator)`

Returns an Optional with the maximum element based on the comparator.
Full traversal required; parallelizable.
Flexible for non-natural ordering (e.g., by length for strings).
Returns empty for empty streams.

```java
Optional<Integer> max = numbers.stream().max(Integer::compareTo);
/* Result: Optional[5] */
```
