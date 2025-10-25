✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ ••‣⁎⁕⁜※⁂

# Types Of Exceptions

## ➡️ ClassCastException

- Occurs when you try to cast an object to a class it doesn’t actually belong to.
- The code compiles fine But at runtime, Java refuses the cast and throws an exception.

```java
Object obj = "Hello World"; // A String object
Integer num = (Integer) obj; // Trying to cast String to Integer
```

- This will thow

```
java.lang.ClassCastException: java.lang.String cannot be cast to java.lang.Integer

```

### 🟦 How to Avoid

- Always prefer compile-time type checking (Generics) over runtime type casting.
- Be cautious when dealing with APIs returning Object, like in legacy code or raw collections.

- Use instanceof before casting

```java
  if (obj instanceof Integer) {
    Integer num = (Integer) obj;
}

```

- Use Generics for Type-Safe Collections
- In modern Java, avoid raw types like List — always use List<T>.

```java
List<String> list = new ArrayList<>();
String str = list.get(0); // No cast needed

```
