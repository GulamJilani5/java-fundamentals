🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ isNull vs isPresent

## ➡️ **Objects:**

- java.util.Objects
- `isNull()` returns true if obj == null
- `nonNull()` returns true if obj != null

- **isNull**
  - Error-prone if you forget the check.
  - Commonly used before `Java 8’s` **Optional** was introduced.

`
User user = userRepository.findById(1001); // might return null

if (Objects.isNull(user)) {
System.out.println("User not found");
} else {
System.out.println("User name: " + user.getName());
}

`

## ➡️ **Optional**

- **isPresent**

  - (modern way) [ Find more in the java8 version section]

- **Method 1**

`
Optional<User> userOpt = userRepository.findByIdOptional(1001);

if (userOpt.isPresent()) {
System.out.println("User name: " + userOpt.get().getName());
} else {
System.out.println("User not found");
}

`

- **Method 2**
  - Better than Method 1

`System.out.println(userOpt.map(User::getName).orElse("User not found"));`

- **Method 3**
  - slightly(both are modern) better than mehtod 2

`Optional<User> userOpt = userRepository.findByIdOptional(1001);
userOpt.ifPresentOrElse(
u -> System.out.println("User name: " + u.getName()),
() -> System.out.println("User not found")
);
`

## ➡️ == vs equals in java

| **Aspect**      | **`==`**                  | **`.equals()`**                        |
| --------------- | ------------------------- | -------------------------------------- |
| **Works on**    | Primitives & Objects      | Objects only                           |
| **For Objects** | Compares memory addresses | Compares contents (if overridden and ) |
| **Default**     | Reference equality        | Reference equality (unless overridden) |
| **Override?**   | Cannot override           | Can override in a class                |

- **.equals()** is overridden in `value-based classes` where logical equality is more useful than reference equality.
- **Common ones that overrides .equals():** String, all wrapper classes of Primitives, collections, enums.
- In your own classes, you override it if you want two different objects with the same field values to be considered "equal".
