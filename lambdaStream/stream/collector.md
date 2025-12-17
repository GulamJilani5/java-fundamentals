🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ .collect()

- It will either have 1 argument or 3 arguments. 2 Arguments are not allowed.
- 1 argument → Collectors.(high-level)
- 3 arguments → manual (Supplier, Accumulator, Combiner)
- 2 arguments → ❌ does not exist

## 1. ➡️ collect(Collector) - One Argument

### 🟦1.1 toList(), toSet()

- Both will have 0 argument.

```java
  List<String> list =
    stream.collect(Collectors.toList());

```

- Return Type list (List<T>)
- Just give all elements in a List”

```java
  Set<String> set =
    stream.collect(Collectors.toSet());
```

- Return Type is set (Set<T>)
- Give unique values

### 🟦1.2 toMap()

| Argument      | Purpose                   |
| ------------- | ------------------------- |
| keyMapper     | How to create key         |
| valueMapper   | How to create value       |
| mergeFunction | What to do if key repeats |
| mapSupplier   | Which Map to create       |

- Return type Map<K, V>.
- Convert stream → key-value structure.

- **2 arguments**
  - toMap(keyMapper, valueMapper)

```java
Map<Integer, String> map =
    employees.stream()
             .collect(Collectors.toMap(
                 Employee::getId,
                 Employee::getName
             ));

```

- **3 arguments**

  - toMap(keyMapper, valueMapper, mergeFunction)

- handle duplicate keys

```java
  Map<String, Integer> map =
    employees.stream()
             .collect(Collectors.toMap(
                 Employee::getDepartment,
                 Employee::getSalary,
                 Integer::max   // merge function
             ));

```

- **4 arguments**
  - toMap(keyMapper, valueMapper, mergeFunction, mapSupplier)

```java

Map<String, Integer> map =
    employees.stream()
             .collect(Collectors.toMap(
                 Employee::getDepartment,    // key mapper
                 Employee::getSalary,        // value mapper
                 Integer::sum,               // merge duplicate keys
                 LinkedHashMap::new          // map implementation
             ));

```

### 🟦1.4 groupingBy()

| Argument    | Purpose                   |
| ----------- | ------------------------- |
| classifier  | How to group              |
| mapSupplier | Which Map implementation  |
| downstream  | What to collect per group |

- Return Type Map<K, D>, K = group key, D = downstream result.
- Group elements into buckets

- **1 arguments**
  - groupingBy(classifier)

```java
  Map<String, List<Employee>> map =
    employees.stream()
             .collect(Collectors.groupingBy(
              Employee::getDepartment
     ));
```

- **2 arguments**

  - groupingBy(classifier, downstream)

- This code is valid

```java
 Map<String, Long> map =
    employees.stream()
             .collect(Collectors.groupingBy(
                 Employee::getDepartment,
                 Collectors.counting()
             ));

```

- This is not valid
- `Collectors.groupingBy` does not have an overload that takes exactly two arguments where the second is a map supplier (like LinkedHashMap::new).

```java
  Map<String, Long> map = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDepartment,     // classifier
        LinkedHashMap::new         // map supplier
    ));
```

- **3 arguments**
  - groupingBy(classifier, mapSupplier, downstream)

```java
 Map<String, Long> map =
    employees.stream()
             .collect(Collectors.groupingBy(
                 Employee::getDepartment,    // classifier
                 LinkedHashMap::new,         // map supplier
                 Collectors.counting()       // downstream collector
             ));

```

### 🟦1.5 partitioningBy()

- Return type Map<Boolean, List<T>>

- **1 argument**
  - partitioningBy(predicate)

```java
 Map<Boolean, List<Employee>> map =
    employees.stream()
             .collect(Collectors.partitioningBy(
                 e -> e.getSalary() > 50000
             ));

```

- **2 arguments**
  - partitioningBy(predicate, downstream)

```java
  Map<Boolean, Long> map =
    employees.stream()
             .collect(Collectors.partitioningBy(
                 e -> e.getSalary() > 50000,
                 Collectors.counting()
             ));
```

### 🟦1.6 counting()

- Does not take any arguments.
- Return type Long.

```java
 long count =
    stream.collect(Collectors.counting());
```

### 🟦1.7 joining()

- Return type is String
- Concatenate strings

- **1 arguments**

  - joining()

```java
  String result =
    Stream.of("Java", "Spring", "Boot")
          .collect(Collectors.joining());
```

- **2 arguments**

  - joining(delimiter)

```java
  String names =
    employees.stream()
             .map(Employee::getName)
             .collect(Collectors.joining(", "));
```

- **3 arguments**
  - joining(delimiter, prefix, suffix)

```java
  String result =
    Stream.of("Java", "Spring", "Boot")
          .collect(Collectors.joining(", ", "[", "]"));
```

- **Output:** [Java, Spring, Boot]

### 🟦1.8 summing

- Numeric aggregation
- summingInt / summingLong / summingDouble
- Return types `int / long / double`
- **1 argument (mapper)**

```java
  int total =
    employees.stream()
             .collect(Collectors.summingInt(Employee::getSalary));
```

### 🟦1.9 averaging

- Numeric aggregation
- averagingInt / averagingLong / averagingDouble
- Return types `int / long / double`
- **1 argument (mapper)**

```java
  double avg =
    employees.stream()
             .collect(Collectors.averagingInt(Employee::getSalary));
```

### 🟦1.10 maxBy / minBy

- Find extreme element
- Return type `Optional<T>`
- **1 argument (Comparator)** maxBy(Comparator), minBy(Comparator)

```java
  Optional<Employee> max =
    employees.stream()
             .collect(Collectors.maxBy(
                 Comparator.comparing(Employee::getSalary)
             ));
```

### 🟦1.11 mapping()

- Transform elements inside grouping
- Return type Depends on downstream
- **2 arguments**, mapping(mapper, downstream)

```java
 Map<String, List<String>> map =
    employees.stream()
             .collect(Collectors.groupingBy(
                 Employee::getDepartment,
                 Collectors.mapping(
                     Employee::getName,
                     Collectors.toList()
                 )
             ));
```

### 🟦1.12 reducing()

- Manual reduce inside collect

- **1 argument (mapper)**
  - reducing(BinaryOperator)
  - - Return type Optional<T>.

```java
  Optional<Integer> result =
    Stream.of(10, 20, 30)
          .collect(Collectors.reducing(
              Integer::sum
          ));

```

- **2 argument (mapper)**
  - reducing(identity, BinaryOperator)
  - Return type is T

```java
  int result =
    Stream.of(10, 20, 30)
          .collect(Collectors.reducing(
              0,
              Integer::sum
          ));

```

- **3 argument (mapper)**
  - reducing(identity, mapper, BinaryOperator)
  - Return type T
  - Replacement for `summingInt`

```java
  int totalSalary =
    employees.stream()
             .collect(Collectors.reducing(
                 0,                      // identity
                 Employee::getSalary,    // mapper
                 Integer::sum            // accumulator
             ));
```

### 🟦1.13 collectingAndThen()

```java
  List<String> unmodifiable =
    stream.collect(
        Collectors.collectingAndThen(
            Collectors.toList(),
            Collections::unmodifiableList
        )
    );
```

## 2.➡️ collect(Supplier, Accumulator, Combiner) - Three Argument

### 🟦 Supplier — creates the result container

- What empty object should I start with?
  - ArrayList::new
  - HashSet::new
  - StringBuilder::new
  - HashMap::new

### 🟦 Accumulator — adds ONE stream element into container

- How do I put a stream element into the container?
  - List::add
  - Set::add
  - StringBuilder::append
  - (map, e) -> map.put(e.getId(), e.getName())

### 🟦 Combiner — merges TWO containers

- If two containers are created (parallel stream),
  how do I merge them?
  - List::addAll
  - Set::addAll
  - StringBuilder::append
  - Map::putAll
