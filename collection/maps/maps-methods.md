🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣

# ✅ Different Ways to Create a Map in Java

### 1. Using HashMap (most common)
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 1);
map.put("B", 2);
```

### 2. Using Map.of() (Java 9+)
- Immutable map.
```java
  Map<String, Integer> map = Map.of("A", 1, "B", 2);
  // map.put("C", 3); // UnsupportedOperationException
```

### 3. Using Map.ofEntries() (Java 9+)
```java
Map<String, Integer> map = Map.ofEntries(
Map.entry("A", 1),
Map.entry("B", 2)
);
```
### 4. Using Streams (Java 8+)
```java
Map<String, Integer> map = Stream.of(new String[][] {
{ "A", "1" },
{ "B", "2" }
}).collect(Collectors.toMap(data -> data[0], data -> Integer.parseInt(data[1])));
```

### 5. 4. Using Collections.singletonMap()
```java
Map<String, String> map = Collections.singletonMap("A", "Apple");
```


-------
# ✅ Map Methods

### Basic Methods
| Method                                   | Description                                                             |
| ---------------------------------------- | ----------------------------------------------------------------------- |
| `put(K key, V value)`                    | Adds a key-value pair to the map. Replaces value if key already exists. |
| `get(Object key)`                        | Returns the value for the given key, or `null` if key not found.        |
| `remove(Object key)`                     | Removes the key (and its value) from the map.                           |
| `clear()`                                | Removes all entries from the map.                                       |
| `size()`                                 | Returns the number of key-value pairs.                                  |
| `isEmpty()`                              | Returns `true` if the map has no entries.                               |
| `containsKey(Object key)`                | Returns `true` if the map contains the given key.                       |
| `containsValue(Object value)`            | Returns `true` if the map contains the given value.                     |
| `putAll(Map<? extends K,? extends V> m)` | Copies all mappings from another map.                                   |
| `equals(Object o)`                       | Compares this map to another.                                           |
| `hashCode()`                             | Returns hash code of the map.                                           |

### 🔁 View Methods (return Collection views)
| Method       | Description                                |
| ------------ | ------------------------------------------ |
| `keySet()`   | Returns a `Set` view of the keys.          |
| `values()`   | Returns a `Collection` view of the values. |
| `entrySet()` | Returns a `Set` of `Map.Entry<K,V>` pairs. |


### 🔄 Default Methods (Java 8+)

| Method                                            | Description                                      |
| ------------------------------------------------- | ------------------------------------------------ |
| `forEach(BiConsumer<? super K,? super V> action)` | Performs action for each key-value pair.         |
| `getOrDefault(Object key, V defaultValue)`        | Returns the value or a default if key not found. |
