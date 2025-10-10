# Four Pillars of OOP

### Encapsulation
- Bundling data (attributes) and methods that operate on that data within a single unit (class).
- Hiding internal details and exposing only what's necessary (through access modifiers like public, private, protected).
```java
class Vehicle {
    private String model;  // Private field (hidden)
    private int speed;

    // Public methods to access private fields (controlled access)
    public void setModel(String model) {
        this.model = model;
    }

    public String getModel() {
        return model;
    }

    public void accelerate(int increment) {
        speed += increment;
    }

    public int getSpeed() {
        return speed;
    }
}
```

### Abstraction
- Showing only essential features while hiding implementation details.
- Creating simple models of complex reality.
```java
abstract class Vehicle {
    abstract void start();  // Abstract method (no implementation)
    abstract void stop();

    public void displayInfo() {
        System.out.println("This is a vehicle.");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Car starts with a key.");
    }

    @Override
    void stop() {
        System.out.println("Car stops by braking.");
    }
}
```

### Inheritance
- Creating new classes (child/derived classes) from existing ones (parent/base classes).
- Promotes code reuse and establishes relationships between classes.
```java
class Vehicle {  // Parent class
    void move() {
        System.out.println("Vehicle is moving.");
    }
}

class Car extends Vehicle {  // Child class
    void honk() {
        System.out.println("Car honks!");
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.move();  // Inherited from Vehicle
        myCar.honk();  // Own method
    }
}
```

### Polymorphism
- Ability of objects to take on many forms ("poly" = many, "morph" = form).
- Same method name can behave differently in different classes.
- Achieved through method overriding and interfaces.

##### a) Method Overriding (Runtime Polymorphism)
- Same method (sound()) behaves differently based on the actual object type (dynamic binding).
```java
class Vehicle {
    void sound() {
        System.out.println("Vehicle makes a sound.");
    }
}

class Car extends Vehicle {
    @Override
    void sound() {
        System.out.println("Car goes Vroom!");
    }
}

class Bike extends Vehicle {
    @Override
    void sound() {
        System.out.println("Bike goes Brrr!");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v1 = new Car();  // Upcasting
        Vehicle v2 = new Bike();

        v1.sound();  // Output: "Car goes Vroom!"
        v2.sound();  // Output: "Bike goes Brrr!"
    }
}
```

##### b) Method Overloading (Compile-Time Polymorphism)
- Same method name (add), but different parameters.
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 10));       // Calls int version
        System.out.println(calc.add(3.5, 2.5));    // Calls double version
    }
}
```