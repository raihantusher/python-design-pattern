---
title: 'Null object pattern'
...
The Null Object design pattern is used to provide an object that acts as a surrogate or placeholder for another object, and yet, it provides default behavior that does nothing or returns default values. This can help avoid null references or null checks in the code, leading to more robust and maintainable programs.

Here's an example of implementing the Null Object pattern in Python:

```python
# Abstract base class for the object hierarchy
class AbstractObject:
    def do_operation(self):
        pass

# Concrete implementation
class RealObject(AbstractObject):
    def do_operation(self):
        print("RealObject is performing an operation")

# Null object implementation
class NullObject(AbstractObject):
    def do_operation(self):
        pass

def main():
    objects = [RealObject(), NullObject(), RealObject()]

    for obj in objects:
        obj.do_operation()

if __name__ == "__main__":
    main()
```

In this example, we have an `AbstractObject` class representing the base class for the object hierarchy, and `RealObject` and `NullObject` as concrete implementations. The `RealObject` performs a specific operation, while the `NullObject` does nothing when the operation is called.

Using the Null Object pattern, you can safely call methods on objects without needing to check for null references. This pattern is particularly useful in scenarios where you want to provide default behavior for missing or optional objects, such as in caching systems, configuration settings, or optional components.

Keep in mind that the effectiveness of the Null Object pattern depends on the context in which it is used. In some cases, it might make sense to return a meaningful default behavior, while in other cases, a no-op behavior (as shown in the example) might be more appropriate.