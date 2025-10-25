✔️🟦🟣🔵🟢🔴🟡🟠➡️⭕🟠⬛🟩🟪🟫 ➡️ ⏺️ ••‣⁎⁕⁜※⁂

# ⏺️ Java Inheritance & Method Resolution – Deep Dive

## ➡️ 1. Field Hiding vs Method Overriding

- If a subclass defines a field with the same name as the parent, it’s field hiding.
- Access depends on reference type, not object type.

```java
class Parent {
int x = 10;
}

class Child extends Parent {
int x = 20;
}

Parent obj = new Child();
System.out.println(obj.x); // 10 — depends on reference type
```

## ➡️ 2. Final Methods

- Final methods cannot be overridden.
- They’re locked to preserve behavior across inheritance.

```java
class Parent {
final void display() {
System.out.println("Parent display");
}
}
class Child extends Parent {
// void display() {} // ❌ Compile-time error
}
```

## ➡️ 3. Method Hiding vs Method Overriding

- Instance methods are overridden and resolved at runtime.
- Static methods are hidden and resolved at compile time (based on reference type).

```java
class Parent {
static void show() { System.out.println("Parent static"); }
void display() { System.out.println("Parent instance"); }
}
class Child extends Parent {
static void show() { System.out.println("Child static"); }
void display() { System.out.println("Child instance"); }
}

Parent p = new Child();
p.show(); // Parent static (compile-time)
p.display(); // Child instance (runtime)
```

## ➡️ 4. Method Overloading Resolution

- **Overloading** → resolved at compile time (based on argument types).
- **Overriding** → resolved at runtime (based on object type).

## ➡️ 5. Covariant Return Types

- A subclass can override a method and return a subtype of the original return type.

```java
class Parent {
Object getValue() { return "Parent"; }
}

class Child extends Parent {
@Override
String getValue() { return "Child"; } // ✅ Allowed (String ⊂ Object)
}
```

## ➡️ 6. Exception Rules in Overriding

- A subclass can throw narrower exceptions or none at all.
- It cannot throw broader or new checked exceptions.

```java
class Parent {
void readFile() throws IOException {}
}

class Child extends Parent {
@Override
void readFile() throws FileNotFoundException {} // ✅ Allowed
}
```

## ➡️ 7. Static & Final Methods with Parent References

- Static methods → resolved by reference type.
- Final methods → resolved by object type, but cannot be overridden.

## ➡️ 8. Interface vs Class Method Access

- You can only call interface methods via an interface reference.
- If both interface and class have the same method, the class implementation wins.

```java
interface I {
void show();
}

class A implements I {
public void show() { System.out.println("Class show"); }
}

I obj = new A();
obj.show(); // Class show
```

## ➡️ 9. Compile-Time vs Runtime Behavior

| Type                 | Resolution Time |
| -------------------- | --------------- |
| **Fields**           | Compile-time    |
| **Static Methods**   | Compile-time    |
| **Instance Methods** | Runtime         |

## ➡️ 10. Private Methods in Parent Class

- Private methods are not inherited.
- A method with the same signature in the child is not an override, but a new method.

```java
class Parent {
private void greet() { System.out.println("Parent greet"); }
}

class Child extends Parent {
void greet() { System.out.println("Child greet"); } // new method
}
```

## ➡️ 11. Access Modifiers in Overriding

- The subclass cannot reduce the visibility of the overridden method.

```java
class Parent {
protected void show() {}
}
class Child extends Parent {
public void show() {} // ✅ Allowed (broader access)
// private void show() {} ❌ Not allowed
}
```
