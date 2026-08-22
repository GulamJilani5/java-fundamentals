⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ Map Traversing

```java
Map<String, Object> map = new HashMap<>();

map.put("name", "John");
map.put("age", 25);
map.put("city", "Pune");
map.put("active", true);
```

```java
Map<String, Object> map = Map.of(
    "name", "John",
    "age", 25,
    "city", "Pune",
    "active", true
);
```

### ➡️ Map

```java
Set<String> = map.keySet()
```

- List of keys → ["name", "age", "city", "active"]

```java
Collection<Object> = map.values()
```

- List of values → ["John", 25, "Pune", true]

### ➡️ Map.Entry — one pair

```java
Map.Entry<String, Object> entry = map.entrySet();
```

- entry.getKey() ---> String(e.g.: "name")
- entry.getValue() ---> Object(e.g.: "John")

##### 🟦 We can For Loop or ForEach to traverse all the pair

```java
for(Map.Entry<String, Object> entry : map.entrySet()){
    String key = entry.getKey();
    Object value = entry.getValue();
    SOP("Key: "+key+" Value: "+value);
}
```

```java
map.forEach((key, value)->{
    SOP("Key: "+key+" Value: "+value);
})
```

- Return value: void

### ➡️ Stream of Map.Entry — all pairs

```java
Stream<Map.Entry<String, Object>> stream = map.entrySet().stream();
```

```java
Stream<String> keys = stream.map(Map.Entry::getKey);
```

- **Return value:** Stream<String> `"name", "age", "city", "active"`

```java
Stream<Object> values = stream.map(Map.Entry::getValue);
```

- **Return value:** Stream<Object> `"John", 25, "Pune", true`

```java
List<String> keys = stream.map(Map.Entry::getKey).toList();
```

- **Return value:** List<String> ["name", "age", "city", "active"]

```java
List<Object> values = stream.map(Map.Entry::getValue).toList();
```

- **Return value:** List<Object> ["John", 25, "Pune", true]
