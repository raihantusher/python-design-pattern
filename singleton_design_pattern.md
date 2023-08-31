---
title: 'Singleton Design Pattern'
...
The Singleton design pattern ensures that a class has only one instance and provides a global point of access to that instance. It is commonly used when you want to control the instantiation of a class to ensure that only one instance exists throughout the application.

Here's an example of implementing the Singleton pattern in Python:

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
            cls._instance.value = None
        return cls._instance

def main():
    singleton1 = Singleton()
    singleton1.value = "Instance 1"

    singleton2 = Singleton()
    print(singleton2.value)  # Output: "Instance 1"

if __name__ == "__main__":
    main()
```

In this example, we have a `Singleton` class with a private class variable `_instance` that holds the single instance of the class. The `__new__` method ensures that only one instance is created and returned, and the `value` attribute can be used to store data specific to the singleton instance.

When you create multiple instances of the `Singleton` class (as `singleton1` and `singleton2` in the example), they both refer to the same instance due to the Singleton pattern. Any changes made to the `value` attribute of one instance are reflected in the other.

Please note that while the above example demonstrates a simple implementation of the Singleton pattern, Python also provides alternative ways of creating singletons using decorators, metaclasses, and module-level variables. Depending on your use case and requirements, you might choose a different approach to implementing the Singleton pattern in Python.