# Functional Interfaces
→ One abstract method (👍required).
→ Any number of default or static methods ➡️(optional).
→ It allows you to use Lambda Expressions and method references.

      @FunctionalInterface
      public interface MyFunction {
          void execute();  // only one abstract method
      }
      ⏺️@FunctionalInterface is optional, but it gives a compile-time check to enforce only one abstract method.

🔵
🟠🔴
•→⁕⁜※✓■

# Built-in(Standard) Functional Interfaces (from 🔵java.util.function package)

| •Interface            | •Method Signature        | •Description                       |
| ----------------------| -----------------------  | -----------------------------------|
| ➡️`Function<T,R>`     | `R apply(T t)`           | Takes input, returns output        |
| ➡️`Predicate<T>`      | `boolean test(T t)`      | Returns true/false                 |
| ➡️`Consumer<T>`       | `void accept(T t)`       | Performs action, returns nothing   |
| ➡️`Supplier<T>`       | `T get()`                | Supplies a value, takes nothing    |
| ➡️`UnaryOperator<T>`  | `T apply(T t)`           | Function where input = output type |
| ➡️`BinaryOperator<T>` | `T apply(T t1, T t2)`    | Takes 2 inputs, returns 1 output   |
| ➡️`BiFunction<T,U,R>` | `R apply(T t, U u)`      | 2 inputs, 1 output                 |
| ➡️`BiPredicate<T,U>`  | `boolean test(T t, U u)` | 2 inputs, true/false               |
| ➡️`BiConsumer<T,U>`   | `void accept(T t, U u)`  | Takes 2 inputs, no return          |

