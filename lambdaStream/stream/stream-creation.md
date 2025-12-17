⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Stream Creation / Converting to Stream (from Source data structure)

- **Java Streams** do not modify the original data source. They operate on a **view** of the data, processing it functionally and immutably. The original collection (**e.g.**, `List`, `Set`) remains unchanged after the stream pipeline finishes.
- If we try to modify the source during stream processing (e.g., via a loop), it can lead to `ConcurrentModificationException`.
- All streams are lazy: They don't process data until a **terminal operation** (e.g., **forEach**, **collect**) is called.

### ➡️ From Collections

- `collection.stream()`

#### 🟦 List (e.g., ArrayList)

- `list.stream()`

#### 🟦 Set (e.g., HashSet)

- set.stream()
- **Sets** do not allow duplicates and have no guaranteed order (unless using **LinkedHashSet** or **TreeSet**).

#### 🟦 Queue (e.g., LinkedList as Queue)

- queue.stream()
- **Queues** follow **FIFO** (First-In-First-Out) order.

#### 🟦 Deque (e.g., ArrayDeque)

- deque.stream()
- **Deques** support insertion/removal from both ends (double-ended queue).

```java
    Deque<String> deque = new ArrayDeque<>();
    deque.addFirst("cherry");  // Add to front
    deque.addLast("apple");    // Add to end
    deque.addLast("banana");

    Stream<String> stream = deque.stream();  // Sequential stream from Deque
    stream.forEach(System.out::println);
```

### ➡️ collection.parallelStream()

- **List**, **Set**, **Queue**, **Deque** and **Map** (as collections) can all be converted to **parallelStream()** in the exact same way as **stream()**

### ➡️ Maps.

- Maps (e.g., HashMap, TreeMap) do not implement the Collection interface, so they cannot be directly converted to streams.
- Instead, use their view methods (keySet(), values(), or entrySet()) to get a Collection view, then call stream() on that view.

#### 🟦 Streaming keys(map.keySet().stream())

```java
Map<String, Integer> map = new HashMap<>();
        map.put("apple", 1);
        map.put("banana", 2);
        map.put("cherry", 3);

        Stream<String> keyStream = map.keySet().stream();  // Stream of keys
        keyStream.forEach(System.out::println);

```

#### 🟦 Streaming Values: map.values().stream()

```java
   Map<String, Integer> map = new HashMap<>();
    map.put("apple", 1);
    map.put("banana", 2);
    map.put("cherry", 3);

    Stream<Integer> valueStream = map.values().stream();  // Stream of values
    valueStream.forEach(System.out::println);
```

#### 🟦 Streaming Entries: map.entrySet().stream()

```java
Map<String, Integer> map = new HashMap<>();
    map.put("apple", 1);
    map.put("banana", 2);
    map.put("cherry", 3);

    Stream<Map.Entry<String, Integer>> entryStream = map.entrySet().stream();  // Stream of entries
    entryStream.forEach(entry -> System.out.println(entry.getKey() + ": " + entry.getValue()));
    // Output: apple: 1 banana: 2 cherry: 3 (order may vary)
```

### ➡️ From Arrays

#### 🟦 Arrays.stream(array)

```java
        String[] array = {"apple", "banana", "cherry"};
        Stream<String> stream = Arrays.stream(array);  // Stream from array
        stream.forEach(System.out::println);
```

#### 🟦 Stream.of(array)

```java
        String[] array = {"apple", "banana", "cherry"};
        Stream<String> stream = Stream.of(array);  // Stream from array
        stream.forEach(System.out::println);
```

- **Arrays.stream(array)** can all be converted to **parallelStream()** in the exact same way as **stream()**

### ➡️ From Values Creating Collections (then Stream)

#### 🟦 Arrays.asList(...)

- Can update elements(set index) but can not add/remove element like size can not be changed.

```java
  List<String> list = Arrays.asList("apple", "banana", "cherry");
  list.stream()
    .forEach(System.out::println);

```

#### 🟦 List.of(...) (Java 9+) Preferred

- Truly immutable, add/remove/update is not possible.

```java
  List<String> list = List.of("apple", "banana", "cherry");
  list.stream()
    .forEach(System.out::println);

```

### ➡️ From Values

- Stream.generate(Supplier)
- Stream.iterate(seed, unaryOperator)
- IntStream.range(1, 10)
- LongStream.rangeClosed(1, 10)
