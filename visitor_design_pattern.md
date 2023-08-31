---
title: 'Visitor design pattern'
...
The Visitor design pattern is used to separate the structure of an object from the operations that can be performed on that object. It allows you to add new operations to an object structure without modifying the objects themselves. This pattern is especially useful when you have a complex object structure and multiple operations that need to be performed on those objects.

Here's an example of implementing the Visitor pattern in Python:

```python
# Visitor interface
class Visitor:
    def visit_circle(self, circle):
        pass

    def visit_square(self, square):
        pass

# Concrete visitor
class AreaVisitor(Visitor):
    def visit_circle(self, circle):
        return 3.14 * circle.radius ** 2

    def visit_square(self, square):
        return square.side ** 2

# Element interface
class Shape:
    def accept(self, visitor):
        pass

# Concrete elements
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def accept(self, visitor):
        return visitor.visit_circle(self)

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def accept(self, visitor):
        return visitor.visit_square(self)

def main():
    shapes = [Circle(5), Square(4)]

    area_visitor = AreaVisitor()

    for shape in shapes:
        area = shape.accept(area_visitor)
        if isinstance(shape, Circle):
            shape_type = "Circle"
        elif isinstance(shape, Square):
            shape_type = "Square"
        print(f"Area of {shape_type}: {area:.2f}")

if __name__ == "__main__":
    main()
```

In this example, we have a `Visitor` interface representing the visitor and a concrete visitor `AreaVisitor` that implements specific operations (calculating area) on concrete elements.

The `Shape` class is the element interface, and `Circle` and `Square` are concrete elements that implement the `accept` method to allow visitors to operate on them.

By using the Visitor pattern, you can add new operations to the object structure (like calculating area in this example) without modifying the classes of the objects themselves. This pattern is particularly useful when you have a complex object structure with multiple operations that can change independently, and you want to avoid tight coupling between the object structure and the operations performed on it.