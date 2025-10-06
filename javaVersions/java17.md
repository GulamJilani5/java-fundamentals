🔵🟢🔴➡️⭕🟠🟦🟣🟥🟧✔️
☑️ • ‣ → ⁕ ⏺️

# ⏺️ Java 17

### ➡️Sealed Classes (Finalized):🟠

- Sealed classes were introduced in **Java 15 (as a preview)** and made stable in **Java 17**.
- A sealed class in Java allows you to control which classes can extend or implement it.
- It provides a middle ground between:
  - final classes → no one can extend
  - normal classes → anyone can extend

#### Key Points

- Declared with sealed keyword.
- Must specify permitted subclasses with permits.
- Subclasses must be either:

  - final → cannot be extended further
  - sealed → can further restrict who can extend
  - non-sealed → removes restrictions and allows anyone to extend further

- Helps in exhaustive pattern matching in switch expressions.
- Encourages well-defined hierarchies, especially in domain models.

#### Shape Hierarchy

```java
// Sealed class
public sealed class Shape permits Circle, Rectangle, Triangle {
    public abstract double area();
}

// Final subclass - no one can extend further
public final class Circle extends Shape {
    private final double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

// Sealed subclass - can further restrict
public sealed class Rectangle extends Shape permits Square {
    protected final double width;
    protected final double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() {
        return width * height;
    }
}

// Final subclass of sealed subclass
public final class Square extends Rectangle {
    public Square(double side) {
        super(side, side);
    }
}

// Non-sealed subclass - anyone can extend it freely
public non-sealed class Triangle extends Shape {
    private final double base;
    private final double height;

    public Triangle(double base, double height) {
        this.base = base;
        this.height = height;
    }

    @Override
    public double area() {
        return 0.5 * base * height;
    }
}

```

##### How to explain in interview

"In Java, a sealed class restricts which other classes can extend or implement it. For example, if I have a Shape class, I can seal it and permit only Circle, Rectangle, and Triangle to extend it. This gives me more control over my class hierarchy and helps avoid unwanted subclasses. Each permitted subclass must declare whether it’s final, sealed, or non-sealed. This is very useful when you want to design APIs or domain models with strict inheritance rules.”

#### Modifiers

| Modifier     | Description                                     |
| ------------ | ----------------------------------------------- |
| `sealed`     | Restricts inheritance to a fixed set of classes |
| `final`      | Prevents further subclassing                    |
| `non-sealed` | Lifts restrictions, allowing anyone to extend   |

### ➡️Pattern Matching for instanceof (Finalized):🟠

### ➡️Vector API (Second Incubator):

### ➡️Foreign Function & Memory API (Incubator):

### ➡️Restore Always-Strict Floating-Point Semantics:

### ➡️Shenandoah Garbage Collector (Production-Ready):🟠

### ➡️Deprecate AOT and JIT Compilation:

### ➡️New macOS Rendering Pipeline:
