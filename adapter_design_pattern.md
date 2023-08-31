---
title: 'Adapter Design Pattern'
keywords:
    - Adapter
    - Design
    - structural design pattern
...
# Adapter Design Pattern
The Adapter design pattern is used to allow two incompatible interfaces to work together. It involves creating a class (the adapter) that acts as a bridge between two interfaces, converting the interface of one class into another interface that clients expect. In other words, it helps to make different classes or components work together seamlessly.

Here's an example of implementing the Adapter pattern in Python:

```python
# Adaptee
class LegacyRectangle:
    def draw(self, x1, y1, x2, y2):
        print(f"Drawing a legacy rectangle: ({x1}, {y1}), ({x2}, {y2})")

# Target interface
class Shape:
    def draw(self):
        pass

# Adapter
class RectangleAdapter(Shape):
    def __init__(self, legacy_rectangle):
        self.legacy_rectangle = legacy_rectangle

    def draw(self):
        x1, y1, x2, y2 = 0, 0, 10, 20
        self.legacy_rectangle.draw(x1, y1, x2, y2)

def main():
    legacy_rectangle = LegacyRectangle()
    rectangle_adapter = RectangleAdapter(legacy_rectangle)

    rectangle_adapter.draw()

if __name__ == "__main__":
    main()
```

In this example, we have a `LegacyRectangle` class with an incompatible interface. We want to use this class in a system that expects objects to implement a `Shape` interface. The `RectangleAdapter` class acts as an adapter, converting the `LegacyRectangle` interface to the `Shape` interface by using composition. It adapts the `draw` method of the `LegacyRectangle` class to work as a `draw` method that conforms to the `Shape` interface.

By using the Adapter pattern, you can integrate new or legacy components into your system without having to modify their existing code. This pattern is especially useful when you're dealing with third-party libraries, legacy code, or when you want to decouple components that have incompatible interfaces.