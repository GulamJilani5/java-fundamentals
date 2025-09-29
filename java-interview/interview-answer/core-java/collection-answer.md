🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

## ➡️ 1. Arrays.asList() vs List.of()

- Java Architecture Insight: List.of() vs Arrays.asList()
- At first glance, they look similar - but their behavior has big design implications

### Arrays.asList ("A""B","C") // fixed-size, updates allowed, no add/remove

`List.of ("A","B""C")`

- add/remove
- fully immutable, no updates, no Design Takeaway

- Null Handling
  `List.of(null)`
- It Throws `NullPointerException`
- Arrays.asList(null)
- null element

`

### Arrays.asList() → update elements, but can't resize.

- safe, truly immutable.
