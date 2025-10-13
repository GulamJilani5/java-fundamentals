🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️ ☑️ • ‣ → ⁕ ⏺️

# ⏺️ Java 8

## ➡️ Lambda Expressions:

- `D:\Jilani\learning\java-fundamentals\lambdaStream\lambda.md`

## ➡️ Stream API:

- `D:\Jilani\learning\java-fundamentals\lambdaStream\stream`

## ➡️ Default Methods in Interfaces:

## ➡️ Method References:

## ➡️ Optional Class:

- `java.util` package that helps handle situations where a value may or may not be present, reducing the risk of `NullPointerException`.

### 🟦 Methods of Optional Class

##### 🔵 Creation

- **Optional.of(T value)**
  - Creates Optional with non-null value (throws NPE if null)
- **Optional.ofNullable(T value)**
  - Creates Optional with given value or empty if null
- **Optional.empty()**
  - Creates an empty Optional

##### 🔵 Checking Presence

- **boolean isPresent()**
  - true if a value is present
- **boolean isEmpty()**
  - true if no value (Java 11+)

##### 🔵 Accessing the Value

- **T get()**
  - Returns value if present, else throws `NoSuchElementException`
- **T orElse(T other)**
  - Returns value if present, otherwise returns other
- **T orElseGet(Supplier<? extends T> supplier)**
  - Returns value if present, otherwise calls supplier
- **<T> T orElseThrow()**
  - Returns value if present, else throws `NoSuchElementException`
- **<T> T orElseThrow(Supplier<? extends X> exceptionSupplier)**
  - Throws custom exception

##### 🔵 Transforming or Chaining

- **map**
  - `<U> Optional<U> map(Function<? super T, ? extends U> mapper) ` Applies a function to the value if present and returns a new Optional with the result, or an empty Optional if no value.
- **flatMap**
  - `<U> Optional<U> flatMap(Function<? super T, Optional<U>> mapper) ` Similar to map, but the function returns an Optional, and the result is not wrapped in another Optional.
- **filter**
  - `Optional<T> filter(Predicate<? super T> predicate) ` Returns an Optional containing the value if it matches the predicate, or an empty Optional.

##### 🔵 Conditional Execution

- **ifPresent(Consumer<? super T> consumer):**
  - Executes the consumer with the value if present.
- **ifPresentOrElse(Consumer<? super T> action, Runnable emptyAction) (Java 9+):**
  - Executes the action if a value is present, or the `emptyAction` if empty.

## ➡️ Date and Time API

## ➡️ Parallel Streams:

## ➡️ Nashorn JavaScript Engine:

## ➡️ Type Annotations:

## ➡️ Metaspace:
