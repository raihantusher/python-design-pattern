---
title: 'Facade Design Pattern'
keywords:
    - facade
    - Structural Design Pattern
...
The Facade design pattern provides a unified interface to a set of interfaces in a subsystem, making it easier for clients to interact with complex systems. It simplifies the usage of a complex system by providing a higher-level interface that abstracts away the underlying complexity. The Facade pattern is particularly useful when dealing with large and intricate systems.

Here's an example of implementing the Facade pattern in Python:

```python
# Subsystem classes
class SubsystemA:
    def method_a(self):
        return "Subsystem A method A"

class SubsystemB:
    def method_b(self):
        return "Subsystem B method B"

class SubsystemC:
    def method_c(self):
        return "Subsystem C method C"

# Facade
class Facade:
    def __init__(self):
        self.subsystem_a = SubsystemA()
        self.subsystem_b = SubsystemB()
        self.subsystem_c = SubsystemC()

    def operation1(self):
        result = []
        result.append(self.subsystem_a.method_a())
        result.append(self.subsystem_b.method_b())
        return "\n".join(result)

    def operation2(self):
        result = []
        result.append(self.subsystem_b.method_b())
        result.append(self.subsystem_c.method_c())
        return "\n".join(result)

def main():
    facade = Facade()

    result1 = facade.operation1()
    print("Operation 1:\n", result1)

    result2 = facade.operation2()
    print("Operation 2:\n", result2)

if __name__ == "__main__":
    main()
```

In this example, we have three subsystem classes (`SubsystemA`, `SubsystemB`, and `SubsystemC`), each with its own methods. The `Facade` class provides a simplified interface to these subsystems, encapsulating their complexities.

The `Facade` class's methods (`operation1` and `operation2`) provide a higher-level interface that internally calls the methods of the subsystems. This way, clients can interact with the complex system using a single, easy-to-understand interface.

By using the Facade pattern, you can improve the usability and readability of your code by providing a simple and clear entry point to a complex system. This is especially useful when you want to shield clients from the inner workings of a subsystem or when you need to refactor or change the subsystems without affecting client code.