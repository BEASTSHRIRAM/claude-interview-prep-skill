# OOPs Reference -- Object Oriented Programming

## The Four Pillars

### 1. Encapsulation
Bundling data (fields) and methods that operate on that data into a single unit (class), and restricting direct access to the internal state.
- Achieved via access modifiers: private, protected, public
- Getters and setters provide controlled access
- Interview angle: "It protects object integrity and reduces coupling between components"

### 2. Abstraction
Hiding the complex implementation details and exposing only what the user needs.
- In Java: achieved via abstract classes and interfaces
- Abstract class: can have method bodies, constructors, fields
- Interface: all methods are implicitly abstract (until Java 8 default methods), no state
- Interview angle: "Abstraction reduces complexity and makes code easier to use and maintain"

### 3. Inheritance
A class (child) inheriting properties and behaviours from another class (parent).
- IS-A relationship: Dog IS-A Animal
- Types: Single, Multilevel, Hierarchical (Java does not support multiple inheritance with classes)
- Method overriding: child provides its own implementation of a parent method
- super keyword: access parent class constructor or method
- Interview angle: "Inheritance promotes code reuse but creates tight coupling, so prefer composition when possible"

### 4. Polymorphism
The ability of an object to take many forms.

**Compile-Time (Static) Polymorphism -- Method Overloading**
Same method name, different parameters (number, type, or order)
```java
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
```

**Run-Time (Dynamic) Polymorphism -- Method Overriding**
Child class overrides parent method. Decision made at runtime via dynamic dispatch.
```java
Animal a = new Dog(); // upcasting
a.sound(); // calls Dog's sound(), not Animal's
```

---

## Interface vs Abstract Class

| Feature | Interface | Abstract Class |
|---|---|---|
| Methods | All abstract (pre Java 8) | Can have concrete and abstract |
| Variables | public static final only | Any type |
| Constructor | Not allowed | Allowed |
| Multiple inheritance | Yes (implements multiple) | No (extends one) |
| Use when | Define a contract/capability | Provide common base with some default behaviour |

---

## SOLID Principles

**S -- Single Responsibility Principle**
A class should have only one reason to change. Each class does one thing well.

**O -- Open Closed Principle**
Open for extension, closed for modification. Add new behaviour via new classes, not by changing existing ones.

**L -- Liskov Substitution Principle**
Objects of a subclass should be replaceable with objects of the superclass without breaking the program.

**I -- Interface Segregation Principle**
No client should be forced to implement methods it does not use. Prefer small, specific interfaces over large general ones.

**D -- Dependency Inversion Principle**
High-level modules should not depend on low-level modules. Both should depend on abstractions (interfaces).

---

## Design Patterns

### Creational Patterns

**Singleton**
Ensures only one instance of a class exists.
```java
public class Singleton {
    private static Singleton instance;
    private Singleton() {}
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```
Thread-safe version uses double-checked locking or enum.

**Factory Method**
Defines an interface for creating objects but lets subclasses decide which class to instantiate.
```java
interface Shape { void draw(); }
class Circle implements Shape { public void draw() { ... } }
class ShapeFactory {
    public static Shape getShape(String type) {
        if (type.equals("circle")) return new Circle();
        // ...
    }
}
```

**Builder**
Constructs complex objects step by step. Avoids telescoping constructors.
```java
Person p = new Person.Builder("Alice").age(22).city("Delhi").build();
```

### Structural Patterns

**Decorator**
Adds behaviour to objects dynamically by wrapping them, without altering the class.
Example: Java I/O streams (BufferedReader wraps FileReader)

**Adapter**
Converts an incompatible interface into one that a client expects.
Example: Power socket adapters in real life

**Facade**
Provides a simplified interface to a complex subsystem.
Example: A hotel reception that coordinates housekeeping, kitchen, and security internally

### Behavioural Patterns

**Observer**
One object (subject) notifies multiple dependents (observers) when its state changes.
Example: YouTube notification system. Event listeners in UI frameworks.

**Strategy**
Defines a family of algorithms and makes them interchangeable.
Example: Sorting strategy, payment strategy (CreditCard, UPI, NetBanking)

**Command**
Encapsulates a request as an object, allowing parameterization, queuing, and undo.
Example: Remote control buttons

---

## Common Interview Questions

1. What is the difference between overloading and overriding?
2. Can we override a static method in Java? (No, static methods are resolved at compile time)
3. Can we override a private method? (No, private methods are not visible to subclasses)
4. What is the diamond problem and how does Java handle it? (Java avoids it by not allowing multiple class inheritance, but interfaces can have default methods, resolved by explicit override)
5. What is an abstract class with no abstract methods? (Valid, prevents direct instantiation)
6. What is covariant return type? (An overriding method can return a subtype of the return type of the overridden method)
7. What is the difference between IS-A and HAS-A relationships?
8. When would you use composition over inheritance? (When you want flexibility and want to avoid tight coupling)
9. What is method hiding vs method overriding? (Static methods are hidden, not overridden)
10. What is the role of the final keyword in OOPs? (final class cannot be inherited, final method cannot be overridden, final variable is a constant)
