⏺️ ➡️ 🟦 🔵 🟢🔴⭕🟠🟣🟥🟧✔️ ☑️ • ‣ → ⁕

# ⏺️ StringUtils

- In Java, **StringUtils** is a utility class for working with Strings.
- It is NOT part of core Java (java.lang). It usually comes from the library.
- Apache Commons Lang Package:
  - `org.apache.commons.lang3.StringUtils`
- Adding StringUtils Dependency

```java
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.14.0</version>
</dependency>
```

### ➡️ Methods

##### 🟦 isEmpty()/isNotEmpty()

- Checks if string is null OR empty ("")

##### 🟦 isBlank()/isNotBlank()

- Checks if string is null, empty, or whitespace.

```java
StringUtils.isBlank(String str)
```

##### 🟦 equals()

- Null-safe comparison.

```java
String a = null;
a.equals("test"); // ❌ NullPointerException

StringUtils.equals(a, "test"); // false
```

##### 🟦 equalsIgnoreCase()

```java
String role = "ADMIN";

if(StringUtils.equalsIgnoreCase(role, "admin")){
    System.out.println("Admin access granted");
}
```

##### 🟦 defaultString()

- Returns default value if null.

```java
String name = null;

String result = StringUtils.defaultString(name);
System.out.println(result); // ""
```

```java
String result = StringUtils.defaultString(name, "Guest");
System.out.println(result); // Guest
```

````

##### 🟦 contains()

- Checks if substring exists.

```java
String text = "Spring Boot Microservices";

System.out.println(StringUtils.contains(text, "Boot")); // true
````

##### 🟦 substring()

- Safe substring.

```java
String str = "SpringBoot";
System.out.println(StringUtils.substring(str, 0, 6)); //Spring
```

##### 🟦 trim() join(), split(), replace(), capitalize()

### ➡️ Very Important methods

- That's why using external library for the string manipulation

##### 🟦 substringAfter()

- Returns the substring after the first occurrence of a separator.

```java
String header = "Bearer token123";

String token = StringUtils.substringAfter(header, " ");
System.out.println(token); //token123
```

- If separator not found

```java
StringUtils.substringAfter("hello", ":") // ""
```

##### 🟦 substringBefore()

- Returns substring before the first occurrence of separator.

```java
String text = "user:john";

String result = StringUtils.substringBefore(text, ":");

System.out.println(result); //user
```

##### 🟦 substringAfterLast()

- Returns substring after the last occurrence.

```java
String file = "report.final.pdf";

String ext = StringUtils.substringAfterLast(file, ".");
System.out.println(ext); //pdf
```

- File extension detection.

##### 🟦 substringBeforeLast()

- Returns substring before the last occurrence.

```java
String file = "report.final.pdf";

String result = StringUtils.substringBeforeLast(file, ".");

System.out.println(result); //report.final
```

##### 🟦 substringBetween()

- Returns substring between two strings.

```java
String text = "Hello [Java] World";

String result = StringUtils.substringBetween(text, "[", "]");

System.out.println(result); //java
```

```java
String html = "<title>My Page</title>";

String title = StringUtils.substringBetween(html, "<title>", "</title>");
System.out.println(title); //My Page
```

##### 🟦 substringsBetween()

- Returns multiple values between delimiters.

```java
String text = "Hello [Java] and [Spring]";

String[] result = StringUtils.substringsBetween(text, "[", "]");

for(String r : result){
    System.out.println(r);  // Java Spring
}
```

##### 🟦 substringAfterAny()

- Returns substring after any of the given separators.

```java
String text = "user=john";

String result = StringUtils.substringAfterAny(text, "=", ":");
System.out.println(result); //john
```

##### 🟦 substringBeforeAny()

- Returns substring before any of the separators.

```java
String text = "john@example.com";

String result = StringUtils.substringBeforeAny(text, "@");
System.out.println(result); //john
```

##### 🟦 removeStart()

- Removes prefix.

```java
String url = "https://google.com";

String result = StringUtils.removeStart(url, "https://");
System.out.println(result); //google.com
```

##### 🟦 removeEnd()

- Removes suffix.

```java
String file = "document.pdf";

String result = StringUtils.removeEnd(file, ".pdf");
System.out.println(result); //document
```
