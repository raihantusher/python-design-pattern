---
title: 'Flyweight Design Pattern'
...
The Flyweight design pattern is used to minimize memory usage and improve performance by sharing common data among multiple objects. It's particularly useful when you have a large number of similar objects that can share some intrinsic state, allowing you to reduce memory consumption and optimize performance.

Here's an example of implementing the Flyweight pattern in Python:

```python
# Flyweight factory
class ShapeFactory:
    _shapes = {}

    @classmethod
    def get_shape(cls, shape_type):
        if shape_type not in cls._shapes:
            if shape_type == "circle":
                cls._shapes[shape_type] = Circle()
            elif shape_type == "square":
                cls._shapes[shape_type] = Square()
            else:
                raise ValueError("Invalid shape type")
        return cls._shapes[shape_type]

# Flyweight interface
class Shape:
    def draw(self, x, y):
        pass

# Concrete flyweight
class Circle(Shape):
    def draw(self, x, y):
        print(f"Drawing a circle at ({x}, {y})")

# Concrete flyweight
class Square(Shape):
    def draw(self, x, y):
        print(f"Drawing a square at ({x}, {y})")

def main():
    shape_factory = ShapeFactory()

    shapes = [
        ("circle", 1, 2),
        ("square", 3, 4),
        ("circle", 5, 6),
    ]

    for shape_type, x, y in shapes:
        shape = shape_factory.get_shape(shape_type)
        shape.draw(x, y)

if __name__ == "__main__":
    main()
```

In this example, we have a `Shape` interface representing the flyweight objects. The `Circle` and `Square` classes are concrete flyweight classes that implement the `Shape` interface.

The `ShapeFactory` class acts as a flyweight factory, managing the creation and sharing of flyweight objects. It uses a dictionary (`_shapes`) to store the instances of flyweight objects. When a client requests a shape, the factory either returns an existing instance from the dictionary or creates a new instance and stores it for future use.

By using the Flyweight pattern, you can greatly reduce memory consumption when dealing with a large number of similar objects. This pattern is particularly useful when the intrinsic state of the objects can be shared among multiple instances, and the extrinsic state (unique state) can be passed as parameters when needed.