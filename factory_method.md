---
title: 'Factory Method'
...
The Factory Method design pattern is a creational pattern that provides an interface for creating objects but allows subclasses to decide which class to instantiate. In Python, you can implement the Factory Method pattern using classes and inheritance. Here's an example of how to implement the Factory Method pattern in Python:

```python
# Abstract Product
class Animal:
    def speak(self):
        pass

# Concrete Products
class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

# Abstract Creator
class AnimalFactory:
    def create_animal(self):
        pass

# Concrete Creators
class DogFactory(AnimalFactory):
    def create_animal(self):
        return Dog()

class CatFactory(AnimalFactory):
    def create_animal(self):
        return Cat()

def main():
    dog_factory = DogFactory()
    cat_factory = CatFactory()

    dog = dog_factory.create_animal()
    cat = cat_factory.create_animal()

    print(dog.speak())  # Output: Woof!
    print(cat.speak())  # Output: Meow!

if __name__ == "__main__":
    main()
```

In this example, we have an abstract `Animal` class and two concrete subclasses `Dog` and `Cat`. We also have an abstract `AnimalFactory` class with two concrete subclasses `DogFactory` and `CatFactory`. Each concrete factory subclass overrides the `create_animal` method to return an instance of the appropriate concrete product.

The `main` function demonstrates how to use the factory methods to create instances of `Dog` and `Cat` without directly instantiating them. This decouples the client code from the concrete product classes, promoting flexibility and easier maintenance.

By following this pattern, you can easily add new types of animals and corresponding factories without modifying existing code. This approach is particularly useful when you want to create objects based on certain conditions or configurations, allowing your code to be more adaptable and extensible.