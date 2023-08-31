---
title: 'Composite Design pattern'
keywords:
    - composite design pattern
    - structural design pattern

...
# Composite Design Pattern
The Composite design pattern is used to create hierarchical structures of objects, treating individual objects and compositions of objects uniformly. It allows clients to work with individual objects and compositions in a consistent manner, without needing to differentiate between them. The Composite pattern is particularly useful when dealing with tree-like structures or complex hierarchies of objects.

Here's an example of implementing the Composite pattern in Python:

```python
# Component
class Graphic:
    def draw(self):
        pass

# Leaf
class Circle(Graphic):
    def draw(self):
        print("Drawing a circle")

# Composite
class CompositeGraphic(Graphic):
    def __init__(self):
        self.graphics = []

    def add(self, graphic):
        self.graphics.append(graphic)

    def remove(self, graphic):
        self.graphics.remove(graphic)

    def draw(self):
        print("Drawing a composite graphic:")
        for graphic in self.graphics:
            graphic.draw()

def main():
    circle1 = Circle()
    circle2 = Circle()
    composite = CompositeGraphic()

    composite.add(circle1)
    composite.add(circle2)

    composite.draw()

if __name__ == "__main__":
    main()
```

In this example, we have a `Graphic` class that represents the component in the composite structure. The `Circle` class is a leaf node in the hierarchy, and the `CompositeGraphic` class represents the composite that can contain other graphics (leaf nodes or other composites).

The `CompositeGraphic` class manages a list of child graphics and implements the `draw` method to draw all the child graphics. This allows you to treat individual circles and composite graphics (combinations of circles) uniformly.

By using the Composite pattern, you can create complex structures of objects while providing a consistent interface for working with them. This pattern is particularly useful for building tree-like structures, such as user interfaces, organizational hierarchies, and any scenario where objects need to be treated as part-whole hierarchies.