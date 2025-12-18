⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ entrySet & Set<Map.Entry<K, V>>

## ➡️ entrySet()

- Returns a `Set<Map.Entry<K, V>>`.
- In simple terms, `entrySet()` converts a **Map** into a **Set** of **Map.Entry** pair objects so that the **Map** can be iterated, streamed, filtered, sorted, or modified.

- `entrySet()` makes a **Map** iterable.

```java
  for (Map.Entry<String, Integer> e : map.entrySet()) {
    System.out.println(e.getKey() + " = " + e.getValue());
}

```

### 🟦 An Example To Understand Properly

- **Example Map**

```java
Map<Integer, String> map = new HashMap<>();
map.put(1, "Alice");
map.put(2, "Bob");
```

- When write `Set<Map.Entry<Integer, String>> set = map.entrySet()`
- It stores objects of type `Map.Entry`

```java
  [
  Entry(key=1, value="Alice"),
  Entry(key=2, value="Bob")
]

```

- Each element in the **Set** is **ONE object** that contains: one key, one value

## ➡️ Map.Entry<K, V>

- `Map.Entry` is a nested interface inside **Map** that represents **one key–value** pair in a Map
- A **Map** stores data like - `key  → value`

  - Each single row inside a **Map** is represented as a **Map.Entry** object.

- **Example Map**

```java
  Map<String, Integer> map = Map.of(
    "Java", 10,
    "Spring", 20
);

```

- Internally, this is seen as:

```java
Entry("Java", 10)
Entry("Spring", 20)

```

- Each of these rows is a **Map.Entry**.
- `Map.Entry<String, Integer> entry = map.entrySet();`

### 🟦 Map.Entry Methods

#### 🔵 Abstract Methods(4 Methods)

- **getKey()**

  ```java
   System.out.println(entry.getKey());
  ```

- **getValue()**
  - Returns the value of the entry

```java
  System.out.println(entry.getValue());  // 10

```

- **setValue(V value)**
  - Replaces the value of the entry
  - Works only for modifiable maps
  - Throws **UnsupportedOperationException** for immutable maps (`Map.of()`).

```java
Map.Entry<String, Integer> entry = map.entrySet().iterator().next();
entry.setValue(30);
```

- **equals(Object o)**
  - Compares both key and value.
  - `(key1.equals(key2)) && (value1.equals(value2))`.

```java
 Map.Entry<String, Integer> e1 = Map.entry("Java", 10);
 Map.Entry<String, Integer> e2 = Map.entry("Java", 10);

 System.out.println(e1.equals(e2)); // true

```

#### 🔵 Static Methods(4 Methods)

##### comparingByKey() & comparingByKey(Comparator<? super K>)

- **comparingByKey()**
  - Returns a **Comparator** that compares entries by key.

```java
  map.entrySet()
   .stream()
   .sorted(Map.Entry.comparingByKey())
   .forEach(System.out::println);

```

- **comparingByKey(Comparator<? super K>)**
  - Custom key comparison

```java
map.entrySet()
   .stream()
   .sorted(Map.Entry.comparingByKey(String.CASE_INSENSITIVE_ORDER))
   .forEach(System.out::println);


```

##### comparingByValue() & comparingByValue(Comparator<? super V>)

- **comparingByValue()**
  - Returns a **Comparator** that compares entries by value.

```java

map.entrySet()
   .stream()
   .sorted(Map.Entry.comparingByValue())
   .forEach(System.out::println);


```

- **comparingByValue(Comparator<? super V>)**
  - Custom value comparison.

```java
map.entrySet()
   .stream()
   .sorted(Map.Entry.comparingByValue(Comparator.reverseOrder()))
   .forEach(System.out::println);


```

#### 🔵 Default Methods(2 Methods)

- **hashCode()**
  - Returns hash code of entry.

```java
  Objects.hashCode(key) ^ Objects.hashCode(value)

```
