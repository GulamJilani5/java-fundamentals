⏺️ ➡️ 🟦 🔵 🟢 🔴 ⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ➡️

```java
List<String> names = Arrays.asList("java", "stream", "api", "java", "code");

String result = names.stream() .distinct() .sorted(Comparator.comparingInt (String::length).reversed()).limit(2).collect(Collectors.joining(", "));
System.out.printIn(result);

```

# ➡️

```java
String input = "AAABBACCDDBBA";

String result = IntStream.range(0, input.length())
        .boxed()
        .filter(i -> i == 0 || input.charAt(i) != input.charAt(i - 1))
        .map(i -> {
            char ch = input.charAt(i);
            long count = IntStream.range(i, input.length())
                    .takeWhile(j -> input.charAt(j) == ch)
                    .count();
            return "" + ch + count;
        })
        .collect(Collectors.joining());

System.out.println(result);
```

# ➡️

```java
  Map.Entry<String, Long> result = employees.stream()
        .filter(emp -> "F".equalsIgnoreCase(emp.getGender()))
        .collect(Collectors.groupingBy(
                Employee::getDepartment,
                Collectors.counting()
        ))
        .entrySet()
        .stream()
        .max(Map.Entry.comparingByValue())
        .orElse(null);

if(result != null){
    System.out.println("Department: " + result.getKey());
    System.out.println("Female Count: " + result.getValue());
}

```
