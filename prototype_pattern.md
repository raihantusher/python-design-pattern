---
title: 'Prototype pattern'
keywords: 
    - prototype pattern
    - prototype
    - creational pattern

...
# Prototype pattern
The Prototype design pattern is used to create new objects by copying an existing object, known as the prototype. This pattern is useful when creating new instances is costly or complex, and you want to avoid creating new objects from scratch. In Python, you can implement the Prototype pattern using the `copy` module or by implementing your own copying mechanism. Here's an example of how to implement the Prototype pattern in Python:

Using the `copy` module:
```python
import copy

# Prototype
class Sheep:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def clone(self):
        return copy.copy(self)

    def __str__(self):
        return f"{self.color} sheep named {self.name}"

def main():
    original_sheep = Sheep("Dolly", "White")
    print("Original:", original_sheep)

    cloned_sheep = original_sheep.clone()
    cloned_sheep.name = "Molly"
    print("Cloned:", cloned_sheep)

if __name__ == "__main__":
    main()
```

Custom copying mechanism:
```python
# Prototype
class Sheep:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def clone(self):
        return Sheep(self.name, self.color)  # Custom copying mechanism

    def __str__(self):
        return f"{self.color} sheep named {self.name}"

def main():
    original_sheep = Sheep("Dolly", "White")
    print("Original:", original_sheep)

    cloned_sheep = original_sheep.clone()
    cloned_sheep.name = "Molly"
    print("Cloned:", cloned_sheep)

if __name__ == "__main__":
    main()
```

In both examples, the `Sheep` class represents the prototype. It has a `clone` method that creates a new object by copying the attributes of the current object. You can use the built-in `copy.copy` function from the `copy` module or implement your own copying mechanism as demonstrated in the custom copying example.

By using the Prototype pattern, you can avoid creating new objects from scratch and improve performance by copying existing instances. This pattern is particularly useful when you have a complex object with multiple attributes, and you want to create variations of it without the overhead of initializing all attributes again.