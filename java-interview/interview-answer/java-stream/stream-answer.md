###

```java
List<String> names = Arrays.asList("java", "stream", "api", "java", "code");

String result = names.stream() .distinct() .sorted(Comparator.comparingInt (String::length).reversed()).limit(2).collect(Collectors.joining(", "));
System.out.printIn(result);

```
