# isNull vs isPresent

- Objects:

  - java.util.Objects
  - `isNull()` returns true if obj == null
  - `nonNull()` returns true if obj != null

- **isNull** - Error-prone if you forget the check.
  - Commonly used before `Java 8’s` **Optional** was introduced.
    `
    User user = userRepository.findById(1001); // might return null

if (Objects.isNull(user)) {
System.out.println("User not found");
} else {
System.out.println("User name: " + user.getName());
}

`

- Optional

  - `isPresent` (modern way) [ Find more in the java8 version section]

- Method 1
  `
  Optional<User> userOpt = userRepository.findByIdOptional(1001);

if (userOpt.isPresent()) {
System.out.println("User name: " + userOpt.get().getName());
} else {
System.out.println("User not found");
}

`

- Method 2
  - Better than Method 1

`System.out.println(userOpt.map(User::getName).orElse("User not found"));`

- Method 3
  - slightly(both are modern) better than mehtod 2

`Optional<User> userOpt = userRepository.findByIdOptional(1001);
userOpt.ifPresentOrElse(
u -> System.out.println("User name: " + u.getName()),
() -> System.out.println("User not found")
);
`
