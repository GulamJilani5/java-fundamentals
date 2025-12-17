🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# Terminal Operations

- Terminal operations in Java Streams are methods that produce a result or side effect from the stream pipeline, triggering the computation and closing the stream.
- 🔴 They don't return another stream, making them the end of the chain. Terminal operations cannot be chained.
- Examples are based on this number list.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```

### ➡️`forEach(Consumer)`

- Return type is **void**, so it's purely for iteration without producing a result.
- 1 argument only e.i consumer
- Applies a given action (consumer) to each element in the stream.
- Primarily used for side effects, like printing or updating external state (not for transforming data).
- Order is preserved for sequential streams; no guarantee for parallel streams.

- **Primitive Example**

```java
numbers.stream().forEach(n -> System.out.print(n + " "));
/* Output: 1 2 3 4 5 */
```

- **Object Example**

```java
 employees.stream()
         .forEach(e -> System.out.println(e.getName()));
```

### ➡️`collect(Collector)`

- Find Answer `D:\Jilani\learning\java-fundamentals\lambdaStream\stream\collector.md`

### ➡️`reduce(...)`

- Reduce stream to single value.
- Return Type
  - With identity → T
  - Without identity → Optional<T>
- Combines elements using an accumulator function to produce a single output value (e.g., sum, product, concatenation).
- **Overloads:** binary operator only (assumes identity like 0 for sum), or with identity and combiner for parallel streams.
- Optional return type if no identity is provided, as the stream might be empty.
- Works best with associative operations for parallelism.

##### 🟦 1 argument - reduce(BinaryOperator<T>)

- **Primitive Example**

```java
 Optional<Integer> sum =
        Stream.of(10, 20, 30)
              .reduce((a, b) -> a + b);

System.out.println(sum.get());   // 60

```

- **Object Example**

```java
 Optional<Employee> highestSalary =
        employees.stream()
                 .reduce((e1, e2) ->
                     e1.getSalary() > e2.getSalary() ? e1 : e2
                 );
highestSalary.ifPresent(System.out::println);


```

##### 🟦 2 argument - reduce(T identity, BinaryOperator<T>)

- **Primitive Example**

```java
int sum =
        Stream.of(10, 20, 30)
              .reduce(0, (a, b) -> a + b);

System.out.println(sum);   // 60

```

- **Object Example**

```java
  Employee defaultEmp = new Employee("NA", 0);

Employee highestSalary =
        employees.stream()
                 .reduce(
                     defaultEmp,
                     (e1, e2) ->
                         e1.getSalary() > e2.getSalary() ? e1 : e2
                 );

System.out.println(highestSalary);

```

##### 🟦 3 argument - reduce(U identity, BiFunction<U,T,U>, BinaryOperator<U>)

- Why 3rd Argument (Combiner) Exists?

  - In parallel stream, data is processed like:

    ````
    Chunk1 → "A,B"
    Chunk2 → "C,D"

        ```
    ````

  - Without combiner → parallel execution fails.

- **Primitive Example**
- Convert Integer stream → String result

```java
 String result =
        Stream.of(1, 2, 3)
              .reduce(
                  "",                         // identity (U)
                  (str, num) -> str + num,    // accumulator
                  (s1, s2) -> s1 + s2         // combiner
              );

System.out.println(result);   // "123"

```

- **Object Example**
- Collect employee names into a single String
  - Stream type → Employee
  - Result type → String

```java
String names =
        employees.stream()
                 .reduce(
                     "",                                      // identity (String)
                     (str, emp) -> str + emp.getName() + ",",
                     (s1, s2) -> s1 + s2
                 );

System.out.println(names);

```

### ➡️`count()`

- Returns Type long.
- Short-circuits if possible but typically traverses the entire stream.
- Efficient for sized sources (e.g., Lists); no side effects.
- Commonly used with filter() to count matches.

- **Primitive Example**

```java
  long c = IntStream.of(1, 2, 3).count();
```

- **Object Example**

```java
  long empCount = employees.stream().count();

```

### ➡️`anyMatch(Predicate)`

- 1 argument only.
- Return type boolean, throws exception if predicate is null.
- Returns true if at least one element matches the predicate; short-circuits on first match.
- Ideal for existence checks without full traversal.
- Works well with parallel streams for early termination.
- **Primitive Example**

```java
 boolean hasEven =
        IntStream.of(1, 3, 5, 6)
                 .anyMatch(n -> n % 2 == 0);

```

- **Object Example**

```java
 boolean hasHR =
        employees.stream()
                 .anyMatch(e -> "HR".equals(e.getDepartment()));

```

### ➡️`allMatch(Predicate)`

- 1 argument only.
- Return type boolean.
- Returns true if every element matches the predicate; short-circuits on first non-match.
- Efficient for validation (e.g., all positive?).
- Parallel-friendly; returns boolean.
- If stream is empty, returns true by default.

- **Primitive Example**

```java
boolean allPositive =
        IntStream.of(1, 2, 3)
                 .allMatch(n -> n > 0);

```

- **Object Example**

```java
  boolean allActive =
        employees.stream()
                 .allMatch(Employee::isActive);

```

### ➡️`noneMatch(Predicate)`

- 1 argument only.
- Return type boolean.
- Returns true if no elements match the predicate; short-circuits on first match (opposite of anyMatch).
- Useful for "absence" checks (e.g., none are negative?).
- Returns boolean; empty stream returns true.
- Complements allMatch for full coverage.
- **Primitive Example**

```java
boolean noneNegative =
        IntStream.of(1, 2, 3)
                 .noneMatch(n -> n < 0);

```

- **Object Example**

```java
  boolean noIntern =
        employees.stream()
                 .noneMatch(e -> e.getRole().equals("Intern"));

```

### ➡️`findFirst()`

- Return type is **Optional<T>**(`OptionalInt / OptionalLong / OptionalDouble`).
- No Argument.
- Returns an Optional with the first element (or empty if none).
- Respects encounter order; short-circuits immediately.
- Preferred for ordered streams; use with limit(1) for unordered.
- Non-deterministic in parallel mode without order.

- **Primitive Example**

```java
OptionalInt first =
        IntStream.of(5, 10, 15).findFirst();

```

- **Object Example**

```java
Optional<Employee> firstEmp =
        employees.stream().findFirst();

```

### ➡️`findAny()`

- Return type is **Optional<T>**.
- No Argument.
- Returns an Optional with any element matching the stream (often first in sequential, arbitrary in parallel).
- Short-circuits on first find; faster for parallel streams.
- Useful when order doesn't matter (e.g., existence in large datasets).
- Returns empty if stream is empty.

- **Primitive Example**

```java
OptionalInt any =
        IntStream.of(1, 2, 3).parallel().findAny();

```

- **Object Example**

```java
 Optional<Employee> anyEmp =
        employees.parallelStream().findAny();

```

### ➡️`min(Comparator)`

- 1 argument only.
- Optional<T> - OptionalInt / OptionalLong / OptionalDouble
- Returns an Optional with the minimum element based on the comparator.
- Traverses the entire stream unless short-circuited (no built-in short-circuit).
- Comparator must be consistent; supports custom ordering.
- Empty stream returns empty Optional.

- **Primitive Example**

```java
 OptionalInt min =
        IntStream.of(3, 1, 5).min();

```

- **Object Example**

```java
 Optional<Employee> minSalary =
        employees.stream()
                 .min(Comparator.comparing(Employee::getSalary));

```

### ➡️`max(Comparator)`

Returns an Optional with the maximum element based on the comparator.
Full traversal required; parallelizable.
Flexible for non-natural ordering (e.g., by length for strings).
Returns empty for empty streams.

- **Primitive Example**

```java
 OptionalInt max =
        IntStream.of(3, 1, 5).max();

```

- **Object Example**

```java
 Optional<Employee> maxSalary =
        employees.stream()
                 .max(Comparator.comparing(Employee::getSalary));

```

### ➡️`toArray()`

- Convert stream → array.
- Return Type `Object[]`, `T[]`.
- Overloads: no-arg (uses runtime type via IntFunction), or with a generator for custom array allocation.
- Useful for interop with legacy array-based APIs.
- Preserves order; supports primitive arrays via specialized streams (e.g., IntStream.toArray()).

##### 0 Arguments

- **Primitive Example**

```java
  Object[] arr =
        IntStream.of(1, 2, 3)
                 .boxed()     // int → Integer
                 .toArray();

System.out.println(Arrays.toString(arr));

```

- **Object Example**

```java
Object[] arr =
        employees.stream()
                 .toArray();

Employee e = (Employee) arr[0];   // casting required

```

##### 1 Arguments

- **Primitive Example**

```java
  int[] arr = IntStream.of(1, 2, 3).toArray();

```

```java
  Integer[] arr =
        IntStream.of(1, 2, 3)
                 .boxed()
                 .toArray(Integer[]::new);

System.out.println(Arrays.toString(arr));

```

- **Object Example**

```java
Employee[] empArray =
        employees.stream()
                 .toArray(Employee[]::new);

System.out.println(empArray[0].getName());
```
