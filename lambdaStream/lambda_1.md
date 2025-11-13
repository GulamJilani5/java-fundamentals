# Interface

An interface in Java is a reference type that defines a contract: a set of methods that must be implemented
by any class that claims to "implement" it.

### ➡️Key Features:

- **until Java 7:** `Only abstract methods`
- **From Java 8+:** `default methods (with body)`, `static methods`
- **From Java 9+:** `private methods` allowed
- Cannot have constructors or instance variables (except public static final constants)

# Abstract Class

An abstract class is a class that cannot be instantiated. It can have abstract methods (without body)
and concrete methods (with body).

### ➡️Key Features:

- Can have constructors.
- Can have instance variables.
- Can have both abstract and non-abstract methods.
- Supports inheritance.
- Allows code reuse via concrete methods.

# Anonymous Class

An anonymous class is a local class without a name. It's used to create a one-time implementation of an
interface or abstract class.

### ➡️Key Features:

- Defined and instantiated in one line.
- Often used with event handling, threading, and functional interfaces.
- Can override methods immediately.
