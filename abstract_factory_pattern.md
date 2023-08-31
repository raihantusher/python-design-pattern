---
title: 'Abstract Factory Pattern'
keywords:
    - factory
    - abrstract
    - creational pattern

...
# Abstract Factor Pattern
The Abstract Factory design pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes. In Python, you can implement the Abstract Factory pattern using classes and inheritance. Here's an example of how to implement the Abstract Factory pattern in Python:

```python
# Abstract Products
class Button:
    def paint(self):
        pass

class Checkbox:
    def paint(self):
        pass

# Concrete Products for Windows
class WindowsButton(Button):
    def paint(self):
        return "Rendering a Windows button"

class WindowsCheckbox(Checkbox):
    def paint(self):
        return "Rendering a Windows checkbox"

# Concrete Products for Mac
class MacButton(Button):
    def paint(self):
        return "Rendering a Mac button"

class MacCheckbox(Checkbox):
    def paint(self):
        return "Rendering a Mac checkbox"

# Abstract Factory
class GUIFactory:
    def create_button(self):
        pass

    def create_checkbox(self):
        pass

# Concrete Factories
class WindowsFactory(GUIFactory):
    def create_button(self):
        return WindowsButton()

    def create_checkbox(self):
        return WindowsCheckbox()

class MacFactory(GUIFactory):
    def create_button(self):
        return MacButton()

    def create_checkbox(self):
        return MacCheckbox()

def create_gui(factory):
    button = factory.create_button()
    checkbox = factory.create_checkbox()
    return button, checkbox

def main():
    windows_factory = WindowsFactory()
    mac_factory = MacFactory()

    windows_button, windows_checkbox = create_gui(windows_factory)
    mac_button, mac_checkbox = create_gui(mac_factory)

    print(windows_button.paint())  # Output: Rendering a Windows button
    print(windows_checkbox.paint())  # Output: Rendering a Windows checkbox

    print(mac_button.paint())  # Output: Rendering a Mac button
    print(mac_checkbox.paint())  # Output: Rendering a Mac checkbox

if __name__ == "__main__":
    main()
```

In this example, we have abstract `Button` and `Checkbox` classes, and two sets of concrete product classes (`WindowsButton`, `WindowsCheckbox` and `MacButton`, `MacCheckbox`). We also have an abstract `GUIFactory` class with two concrete subclasses (`WindowsFactory` and `MacFactory`). Each concrete factory subclass overrides the `create_button` and `create_checkbox` methods to return instances of the appropriate concrete products.

The `create_gui` function demonstrates how to use the abstract factory to create a family of related objects without specifying their concrete classes. This allows you to create GUI elements for different platforms (Windows and Mac) without tightly coupling the client code to specific implementations.

By following this pattern, you can easily switch between different sets of related objects by changing the concrete factory you use, providing a way to achieve platform-independent and extensible code.