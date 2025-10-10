🔴🔵☑️✔️ ➡️ ✓→•←⁕⁂※⁜‣

# 🔁 Several Ways to Loop Over a Map in Java

### 1.  Using entrySet() with enhanced for-loop
```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
System.out.println(entry.getKey() + " = " + entry.getValue());
}
```

### 2. Using keySet() and get()
```java
for (String key : map.keySet()) {
System.out.println(key + " = " + map.get(key));
}
```


### 3. Using values()
```java
for (Integer value : map.values()) {
System.out.println(value);
}
```


### 4. Using forEach() and lambda (Java 8+)
```java
map.forEach((key, value) -> System.out.println(key + " = " + value));
```

### 5. Using Stream API
```java
map.entrySet().stream()
.forEach(entry -> System.out.println(entry.getKey() + " = " + entry.getValue()));
```



### 6. Using Iterator
```java
Iterator<Map.Entry<String, Integer>> iterator = map.entrySet().iterator();
while (iterator.hasNext()) {
Map.Entry<String, Integer> entry = iterator.next();
System.out.println(entry.getKey() + " = " + entry.getValue());
}
```


