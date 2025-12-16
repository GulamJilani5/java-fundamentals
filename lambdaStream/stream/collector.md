🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ .collect()

- It will either have 1 argument or 3 arguments. 2 Arguments are not allowed.
- 1 argument → Collectors.(high-level)
- 3 arguments → manual (Supplier, Accumulator, Combiner)
- 2 arguments → ❌ does not exist

## ➡️ collect(Collector) - One Argument

### 🟦 toList()

```java
  List<String> list =
    stream.collect(Collectors.toList());
```

### 🟦 toSet()

```java
  Set<String> set =
    stream.collect(Collectors.toSet());
```

### 🟦 toMap()

```java
Map<Integer, String> map =
    stream.collect(Collectors.toMap(
        User::getId,
        User::getName
    ));
```

```java
toMap(keyMapper, valueMapper)
toMap(keyMapper, valueMapper, mergeFunction)
toMap(keyMapper, valueMapper, mergeFunction, mapSupplier)

```

### 🟦 groupingBy()

```java
 Map<String, List<Employee>> map =
    employees.stream()
             .collect(Collectors.groupingBy(Employee::getDepartment));
```

### 🟦 partitioningBy()

```java
 Map<Boolean, List<Employee>> map =
    employees.stream()
             .collect(Collectors.partitioningBy(
                 e -> e.getSalary() > 50000
             ));
```

### 🟦 counting()

```java
 long count =
    stream.collect(Collectors.counting());
```

### 🟦 joining()

```java
  String names =
    employees.stream()
             .map(Employee::getName)
             .collect(Collectors.joining(", "));
```

### 🟦 summing

- summingInt / summingLong / summingDouble

```java
  int total =
    employees.stream()
             .collect(Collectors.summingInt(Employee::getSalary));
```

### 🟦 averaging

- averagingInt / averagingLong / averagingDouble

```java
  double avg =
    employees.stream()
             .collect(Collectors.averagingInt(Employee::getSalary));
```

### 🟦 maxBy / minBy

```java
  Optional<Employee> max =
    employees.stream()
             .collect(Collectors.maxBy(
                 Comparator.comparing(Employee::getSalary)
             ));
```

### 🟦 mapping()

```java
  Map<String, List<String>> map =
    employees.stream()
             .collect(Collectors.groupingBy(
                 Employee::getDepartment,
                 Collectors.mapping(Employee::getName, Collectors.toList())
             ));
```

### 🟦 reducing()

```java
  int sum =
    stream.collect(Collectors.reducing(0, Integer::sum));
```

### 🟦 collectingAndThen()

```java
  List<String> unmodifiable =
    stream.collect(
        Collectors.collectingAndThen(
            Collectors.toList(),
            Collections::unmodifiableList
        )
    );
```

## ➡️ collect(Supplier, Accumulator, Combiner) - Three Argument

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
