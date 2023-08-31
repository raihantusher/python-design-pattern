---
title: 'Design Pattern '
keywords:
    - design pattern
    - all design pattern

...
# Design Pattern
There are many design patterns in object-oriented programming (OOP) that help to solve common software design problems. Here's a list of some well-known design patterns categorized into three groups: Creational, Structural, and Behavioral.

**Creational Design Patterns:**

1.  **Singleton:** Ensures a class has only one instance and provides a global point of access to that instance.
2.  **Factory Method:** Defines an interface for creating objects but allows subclasses to decide which class to instantiate.
3.  **Abstract Factory:** Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
4.  **Builder:** Separates the construction of a complex object from its representation, allowing the same construction process to create different representations.
5.  **Prototype:** Creates new objects by copying an existing object, thus avoiding the need to create subclasses of an object.

**Structural Design Patterns:**

1.  **Adapter:** Converts the interface of a class into another interface that clients expect. Allows classes with incompatible interfaces to work together.
2.  **Bridge:** Separates an abstraction from its implementation, allowing both to evolve independently.
3.  **Composite:** Composes objects into tree structures to represent part-whole hierarchies. Clients can treat individual objects and compositions of objects uniformly.
4.  **Decorator:** Adds responsibilities to objects dynamically, providing a flexible alternative to subclassing for extending functionality.
5.  **Facade:** Provides a unified interface to a set of interfaces in a subsystem. Simplifies the usage of complex systems.
6.  **Flyweight:** Shares objects to support a large number of fine-grained objects efficiently.
7.  **Proxy:** Provides a surrogate or placeholder for another object to control access, add additional behavior, or delay instantiation.

**Behavioral Design Patterns:**

1.  **Chain of Responsibility:** Avoids coupling the sender of a request to its receiver by allowing more than one object to handle the request.
2.  **Command:** Turns a request into a stand-alone object, containing all the information about the request. This decouples sender and receiver.
3.  **Interpreter:** Provides a way to evaluate language grammar or expressions.
4.  **Iterator:** Provides a way to access elements of a collection without exposing its underlying representation.
5.  **Mediator:** Reduces direct connections between classes by having them communicate through a central mediator object.
6.  **Memento:** Allows an object's state to be captured and restored later, without revealing its internal structure.
7.  **Observer:** Defines a dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
8.  **State:** Allows an object to change its behavior when its internal state changes.
9.  **Strategy:** Defines a family of algorithms, encapsulates them, and makes them interchangeable. Clients can switch algorithms without altering the class that uses them.
10. **Template Method:** Defines the structure of an algorithm but allows subclasses to override specific steps.
11. **Visitor:** Separates an algorithm from an object structure, allowing new operations to be added without modifying the objects.

Please note that this list covers some of the most commonly known design patterns. There might be other patterns and variations as well. Each design pattern addresses a specific set of design challenges, so it's important to choose the appropriate pattern based on the problem you're trying to solve.