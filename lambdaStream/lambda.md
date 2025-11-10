#  Interface
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

# Functional Interfaces
- One abstract method (👍required).
- Any number of default or static methods ➡️(optional).
- It allows you to use Lambda Expressions and method references.

```java
@FunctionalInterface
public interface MyFunction {
    void execute();  // only one abstract method
}
```
- @FunctionalInterface is optional, but it gives a compile-time check to enforce only one abstract method.

# Built-in(Standard) Functional Interfaces (from 🔵java.util.function package)

| Interface             | Method Signature        | Description                       |
|-----------------------| -----------------------  | ----------------------------------|
| ➡️`Function<T,R>`     | `R apply(T t)`          | Takes input, returns output       |
| ➡️`Predicate<T>`      | `boolean test(T t)`     | Returns true/false                |
| ➡️`Consumer<T>`       | `void accept(T t)`      | Performs action, returns nothing  |
| ➡️`Supplier<T>`       | `T get()`               | Supplies a value, takes nothing   |
| ➡️`UnaryOperator<T>`  | `T apply(T t)`          | Function where input = output type |
| ➡️`BinaryOperator<T>` | `T apply(T t1, T t2)`   | Takes 2 inputs, returns 1 output  |
| ➡️`BiFunction<T,U,R>` | `R apply(T t, U u)`     | 2 inputs, 1 output                |
| ➡️`BiPredicate<T,U>`  | `boolean test(T t, U u)` | 2 inputs, true/false              |
| ➡️`BiConsumer<T,U>`   | `void accept(T t, U u)` | Takes 2 inputs, no return         |


# Lambda Function and Lambda Expressions

### ➡️Lambda Expression (Definition/Syntax)
- Refers to the syntax/code construct used to declare an anonymous function.
- It’s the actual code written using the -> syntax.
- It doesn’t exist on its own – it must be assigned to a variable or passed to a method expecting a 
             functional interface.
### ➡️Lambda Function (Executable Entity)
- Refers to the actual instance of a function created from a lambda expression.
- It's a function object that implements a functional interface.
- When you assign a lambda expression to a functional interface, you get a lambda function.

| Concept          | Lambda Expression         | Lambda Function                                                |
| ---------------- | ------------------------- | -------------------------------------------------------------- |
| What is it?      | Code syntax using `->`    | Actual object created from the expression                      |
| Executable?      | ❌ No                      | ✅ Yes, it implements a functional interface                    |
| Example          | `(a, b) -> a + b`         | `BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;` |
| Needs interface? | ❌ Not by itself           | ✅ Must be assigned to a functional interface                   |
| Comparable to    | A **function definition** | A **function instance** or **object**                          |

  
### ➡️Different ways to create the  lambda expression  
     
##### 1. No Parameter Lambda
- Used when the method has no arguments.
- Often used with Runnable, event listeners, etc.
**Example:** 
```java
Runnable r = () -> System.out.println("Hello World");
r.run();
```
                
##### 2. Single Parameter Lambda
- If only one parameter, parentheses are optional
**Example:**
```java
 Consumer<String> printer = message -> System.out.println(message);
 printer.accept("Lambda with one parameter");
 ```
##### 3. Multiple Parameters Lambda
- Parentheses required when there is more than one parameter.
**Example:**
```java
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
System.out.println(add.apply(5, 10)); // Output: 15
```

##### 4. With Block Body (Curly Braces and Return)
- Use this when the logic has multiple lines or return statements.
  **Example:**
```java
Function<Integer, String> evenOdd = (n) -> {
   if (n % 2 == 0) return "Even";
   else return "Odd";
};
System.out.println(evenOdd.apply(4)); // Even

```
##### 5. Without Return (Single-Line Expression)
- For simple expressions, Java infers return value automatically.
        **Example:** 
        
```java                   
Predicate<Integer> isPositive = x -> x > 0;
System.out.println(isPositive.test(5)); // true
 ```

##### 6. With Type Declaration (Optional)
- Type is usually inferred, but can be explicitly declared.
**Example:** 
```java
BinaryOperator<Integer> multiply = (Integer a, Integer b) -> a * b;
System.out.println(multiply.apply(3, 4)); // 12
```
##### 7. Returning a Lambda (Higher-order style)
- You can return lambdas from methods (higher-order functions).
**Example:** 
```java
public static Function<Integer, Integer> multiplier(int x) {
    return (n) -> n * x;
 }
Function<Integer, Integer> times3 = multiplier(3);
System.out.println(times3.apply(10)); // 30
```








