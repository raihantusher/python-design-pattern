---
title: 'Builder Pattern'
keywords:
    - builder pattern
    - creational pattern
    - builder

...
# Builder Design Pattern
The Builder design pattern is used to construct complex objects step by step. It separates the construction of a complex object from its representation, allowing the same construction process to create different representations. In Python, you can implement the Builder pattern using classes and methods. Here's an example of how to implement the Builder pattern in Python:

```python
# Product
class Pizza:
    def __init__(self):
        self.crust = ""
        self.sauce = ""
        self.toppings = []

    def __str__(self):
        return f"Crust: {self.crust}, Sauce: {self.sauce}, Toppings: {', '.join(self.toppings)}"

# Abstract Builder
class PizzaBuilder:
    def build_crust(self):
        pass

    def build_sauce(self):
        pass

    def build_toppings(self):
        pass

    def get_pizza(self):
        pass

# Concrete Builders
class MargheritaPizzaBuilder(PizzaBuilder):
    def __init__(self):
        self.pizza = Pizza()

    def build_crust(self):
        self.pizza.crust = "Thin Crust"

    def build_sauce(self):
        self.pizza.sauce = "Tomato Sauce"

    def build_toppings(self):
        self.pizza.toppings.append("Mozzarella Cheese")
        self.pizza.toppings.append("Basil")

    def get_pizza(self):
        return self.pizza

class PepperoniPizzaBuilder(PizzaBuilder):
    def __init__(self):
        self.pizza = Pizza()

    def build_crust(self):
        self.pizza.crust = "Thick Crust"

    def build_sauce(self):
        self.pizza.sauce = "Tomato Sauce"

    def build_toppings(self):
        self.pizza.toppings.append("Pepperoni")
        self.pizza.toppings.append("Mozzarella Cheese")

    def get_pizza(self):
        return self.pizza

# Director
class Waiter:
    def __init__(self):
        self.builder = None

    def set_builder(self, builder):
        self.builder = builder

    def construct_pizza(self):
        self.builder.build_crust()
        self.builder.build_sauce()
        self.builder.build_toppings()

    def get_pizza(self):
        return self.builder.get_pizza()

def main():
    waiter = Waiter()

    margherita_builder = MargheritaPizzaBuilder()
    pepperoni_builder = PepperoniPizzaBuilder()

    waiter.set_builder(margherita_builder)
    waiter.construct_pizza()
    margherita_pizza = waiter.get_pizza()
    print("Margherita Pizza:", margherita_pizza)

    waiter.set_builder(pepperoni_builder)
    waiter.construct_pizza()
    pepperoni_pizza = waiter.get_pizza()
    print("Pepperoni Pizza:", pepperoni_pizza)

if __name__ == "__main__":
    main()
```

In this example, we have a `Pizza` class representing the product being built. We also have an abstract `PizzaBuilder` class with concrete subclasses (`MargheritaPizzaBuilder` and `PepperoniPizzaBuilder`) representing the different ways to build a pizza.

The `Waiter` class acts as a director and controls the construction process. It has a method to set a specific builder and another method to construct the pizza step by step.

By using the Builder pattern, you can create complex objects with a clear and organized construction process, making it easier to manage different variations of the product. This pattern is particularly useful when you have complex object creation logic and want to keep the client code separate from the construction details.