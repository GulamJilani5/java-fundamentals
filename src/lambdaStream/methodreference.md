# 1. Lambda Expressions
- concise way to represent anonymous functions (implementations of functional interfaces).
- Used in streams to define custom behavior for operations like map, filter, forEach, etc.
- **Syntax:** `(parameters) -> expression or (parameters) -> { statements; }`
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
numbers.stream()
.map(n -> n * 2) // Lambda: multiplies each number by 2
.forEach(System.out::println);
```
- different ways to create lambda expression is available in the `lambdaStream/lambda`

# 2. Method References
- Shorthand for lambda expressions that invoke existing methods.
- Make code more readable by replacing lambdas with a direct reference to a method.
- **Syntax:** `ClassName::methodName or instance::methodName`

**Four Types of Method References:**
### 1. Static Method Reference: `ClassName::staticMethod`
- **Example:** `Integer::parseInt`
- **Use:** Refers to a static method of a class.
```java
```
### 2. Instance Method Reference (of a specific object): `instance::methodName`
- **Example:** `System.out::println`
- **Use:** Refers to an instance method of a specific object.
```java
List<String> names = Arrays.asList("Alice", "Bob");
names.stream()
     .forEach(System.out::println); // Calls println on System.out
```

### 3. Instance Method Reference (of an arbitrary object): `ClassName::instanceMethod`
- **Example:** `String::toUpperCase`
- **Use:** Refers to an instance method applied to each object in the stream.
```java
List<String> names = Arrays.asList("alice", "bob");
names.stream()
     .map(String::toUpperCase) // Calls toUpperCase on each string
     .forEach(System.out::println);
```

### 4. Constructor Reference: `ClassName::new`
- **Example:** `String::new`
- **Use:** Refers to a constructor for creating new objects.
```java
List<String> values = Arrays.asList("a", "b", "c");
values.stream()
      .map(String::new) // Creates new String objects
      .collect(Collectors.toList());
```


### Combining both Lambda Expression and Method Reference
```java
List<String> names = Arrays.asList("alice", "bob", "charlie");
List<String> result = names.stream()
                          .filter(s -> s.length() > 3) // Lambda: filters strings longer than 3 chars
                          .map(String::toUpperCase)    // Method reference: converts to uppercase
                          .collect(Collectors.toList());
System.out.println(result); // Output: [ALICE, CHARLIE]
```