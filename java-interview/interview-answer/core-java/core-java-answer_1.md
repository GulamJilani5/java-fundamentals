🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Answers

## ➡️ 1. == vs equals in java

| **Aspect**      | **`==`**                  | **`.equals()`**                        |
| --------------- | ------------------------- | -------------------------------------- |
| **Works on**    | Primitives & Objects      | Objects only                           |
| **For Objects** | Compares memory addresses | Compares contents (if overridden and ) |
| **Default**     | Reference equality        | Reference equality (unless overridden) |
| **Override?**   | Cannot override           | Can override in a class                |

- **.equals()** is overridden in `value-based classes` where logical equality is more useful than reference equality.
- **Common ones that overrides .equals():** String, all wrapper classes of Primitives, collections, enums.
- In your own classes, you override it if you want two different objects with the same field values to be considered "equal".
