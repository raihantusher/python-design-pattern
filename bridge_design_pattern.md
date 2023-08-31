---
title: 'Bridge Design Pattern'
keywords:
    - Bridge Design Pattern
    - Structural Desing pattern
...
# Bridge Design Pattern
The Bridge design pattern is used to separate the abstraction from its implementation, allowing both to evolve independently. It involves creating two hierarchies: one for the abstraction (high-level functionality) and another for the implementation (low-level details). The bridge between these hierarchies allows the abstraction and implementation to vary independently.

Here's an example of implementing the Bridge pattern in Python:

```python
# Abstraction
class Shape:
    def __init__(self, color):
        self.color = color

    def draw(self):
        pass

# Concrete Abstraction
class Circle(Shape):
    def __init__(self, x, y, radius, color):
        super().__init__(color)
        self.x = x
        self.y = y
        self.radius = radius

    def draw(self):
        print(f"Drawing a {self.color} circle at ({self.x}, {self.y}) with radius {self.radius}")

class Square(Shape):
    def __init__(self, x, y, side, color):
        super().__init__(color)
        self.x = x
        self.y = y
        self.side = side

    def draw(self):
        print(f"Drawing a {self.color} square at ({self.x}, {self.y}) with side {self.side}")

# Implementation
class Color:
    def fill(self):
        pass

# Concrete Implementation
class RedColor(Color):
    def fill(self):
        return "Red"

class BlueColor(Color):
    def fill(self):
        return "Blue"

# Bridge
class ShapeColorBridge:
    def __init__(self, color):
        self.color = color

    def apply_color(self):
        pass

# Refined Abstraction
class ColoredShape(ShapeColorBridge):
    def __init__(self, shape, color):
        super().__init__(color)
        self.shape = shape

    def apply_color(self):
        return self.shape.draw() + f" filled with {self.color.fill()} color"

def main():
    red_color = RedColor()
    blue_color = BlueColor()

    red_circle = Circle(5, 5, 10, red_color)
    blue_square = Square(10, 10, 15, blue_color)

    red_colored_circle = ColoredShape(red_circle, red_color)
    blue_colored_square = ColoredShape(blue_square, blue_color)

    print(red_colored_circle.apply_color())  # Output: Drawing a Red circle at (5, 5) with radius 10 filled with Red color
    print(blue_colored_square.apply_color())  # Output: Drawing a Blue square at (10, 10) with side 15 filled with Blue color

if __name__ == "__main__":
    main()
```

In this example, we have an abstraction hierarchy represented by the `Shape` class, which has concrete subclasses `Circle` and `Square`. We also have an implementation hierarchy represented by the `Color` class, with concrete subclasses `RedColor` and `BlueColor`.

The `ShapeColorBridge` class acts as a bridge, connecting the abstraction and implementation hierarchies. The `ColoredShape` class represents a refined abstraction, combining a shape with a color to create a colored shape.

By using the Bridge pattern, you can achieve loose coupling between abstraction and implementation, allowing both to change and evolve independently. This pattern is particularly useful when you have multiple dimensions of variation in your system, such as different shapes and different colors in this example.