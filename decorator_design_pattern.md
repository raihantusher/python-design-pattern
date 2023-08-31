---
title: 'Decorator Design Pattern'
keywords:
    - decorator design pattern
    - structural design pattern
...
# Decorator Design Pattern
The Decorator design pattern is used to dynamically add behaviors or responsibilities to objects without altering their code. It involves creating a set of decorator classes that wrap around the original class, allowing you to add or modify functionality in a flexible and reusable way. The Decorator pattern is particularly useful when you want to extend or enhance the behavior of objects at runtime.

Here's an example of implementing the Decorator pattern in Python:

```python
# Component interface
class Coffee:
    def cost(self):
        pass

# Concrete component
class SimpleCoffee(Coffee):
    def cost(self):
        return 5

# Decorator
class CoffeeDecorator(Coffee):
    def __init__(self, coffee):
        self._coffee = coffee

    def cost(self):
        return self._coffee.cost()

# Concrete decorators
class MilkDecorator(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 2

class SugarDecorator(CoffeeDecorator):
    def cost(self):
        return self._coffee.cost() + 1

def main():
    simple_coffee = SimpleCoffee()
    print("Cost of simple coffee:", simple_coffee.cost())

    milk_coffee = MilkDecorator(simple_coffee)
    print("Cost of milk coffee:", milk_coffee.cost())

    sugar_milk_coffee = SugarDecorator(milk_coffee)
    print("Cost of sugar milk coffee:", sugar_milk_coffee.cost())

if __name__ == "__main__":
    main()
```

In this example, we have a `Coffee` interface representing the component, and a `SimpleCoffee` class as the concrete component. The `CoffeeDecorator` class is the decorator, which extends the behavior of the component.

The `MilkDecorator` and `SugarDecorator` classes are concrete decorators that wrap around existing coffee objects and add the cost of milk and sugar, respectively.

By using the Decorator pattern, you can add new functionalities or modify existing ones without altering the original component class. This allows you to create a flexible and reusable system of decorators that can be combined in various ways to achieve different combinations of behavior. This pattern is useful when you have a need for incremental or dynamic extension of object functionality.