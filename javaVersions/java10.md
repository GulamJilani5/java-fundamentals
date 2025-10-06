# var

- The type is obvious from the right-hand side, e.g., var list = new ArrayList<String>();
- It improves readability by avoiding repetition of long generic types.
- You're working with anonymous types (e.g., in streams, lambdas, or complex return types).

| Feature         | `var`                                         |
| --------------- | --------------------------------------------- |
| Introduced in   | Java 10                                       |
| Scope           | Local variables only                          |
| Type            | Inferred at compile time (not dynamic typing) |
| Best used when  | Type is obvious, avoids verbosity             |
| Not allowed for | Fields, parameters, return types, null        |
