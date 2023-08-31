---
title: 'Template method design pattern'
...
The Template Method design pattern is used to define the skeleton of an algorithm in a base class, allowing subclasses to override specific steps of the algorithm while preserving the overall structure. It promotes code reuse and enforces a consistent algorithm structure across multiple subclasses.

Here's an example of implementing the Template Method pattern in Python:

```python
# Abstract class with template method
class AbstractClass:
    def template_method(self):
        self.step1()
        self.step2()
        self.step3()

    def step1(self):
        pass

    def step2(self):
        pass

    def step3(self):
        pass

# Concrete subclass
class ConcreteClassA(AbstractClass):
    def step2(self):
        print("ConcreteClassA: Step 2")

# Concrete subclass
class ConcreteClassB(AbstractClass):
    def step1(self):
        print("ConcreteClassB: Step 1")

    def step2(self):
        print("ConcreteClassB: Step 2")

    def step3(self):
        print("ConcreteClassB: Step 3")

def main():
    concrete_a = ConcreteClassA()
    concrete_b = ConcreteClassB()

    print("Using ConcreteClassA:")
    concrete_a.template_method()

    print("\nUsing ConcreteClassB:")
    concrete_b.template_method()

if __name__ == "__main__":
    main()
```

In this example, we have an `AbstractClass` representing the template with a `template_method` that defines the algorithm's overall structure. The `step1`, `step2`, and `step3` methods are placeholders for steps that can be customized by concrete subclasses.

We have two concrete subclasses, `ConcreteClassA` and `ConcreteClassB`, which provide their own implementations for specific steps.

When the `template_method` is called on a concrete subclass, it invokes the steps in the predefined order, as defined in the base class, while allowing subclasses to override specific steps.

By using the Template Method pattern, you can define a high-level algorithm structure in a base class while enabling subclasses to customize specific steps. This pattern is particularly useful when you want to enforce a common process across multiple subclasses while allowing variations in certain parts of the process.