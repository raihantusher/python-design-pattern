---
title: 'Proxy Design Pattern'
...
The Proxy design pattern is used to provide a surrogate or placeholder for another object to control access to it. It acts as an intermediary that adds an extra level of indirection to control and manage the access to the original object. Proxies can have various purposes, such as controlling access, delaying object creation, providing additional functionality, or caching.

Here's an example of implementing the Proxy pattern in Python:

```python
# Subject interface
class Image:
    def display(self):
        pass

# Real subject
class RealImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.load_image()

    def load_image(self):
        print(f"Loading image: {self.filename}")

    def display(self):
        print(f"Displaying image: {self.filename}")

# Proxy
class ProxyImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.real_image = None

    def display(self):
        if self.real_image is None:
            self.real_image = RealImage(self.filename)
        self.real_image.display()

def main():
    image1 = ProxyImage("image1.jpg")
    image2 = ProxyImage("image2.jpg")

    image1.display()  # Image will be loaded and displayed
    image2.display()  # Image will be loaded and displayed

    image1.display()  # Image will be displayed directly (already loaded)

if __name__ == "__main__":
    main()
```

In this example, we have a `Image` interface representing the subject, a `RealImage` class as the real subject that loads and displays images, and a `ProxyImage` class acting as a proxy.

The `ProxyImage` class delays the creation and loading of the `RealImage` object until the `display` method is called. This way, the image is only loaded when it's actually needed. Additionally, if the image has already been loaded, the proxy simply delegates the `display` call to the real image.

By using the Proxy pattern, you can control access to the real object, add additional functionality (e.g., logging, security checks), or delay the creation of expensive objects until they are needed. This can be particularly useful in scenarios where object creation or access is resource-intensive or where you want to implement a level of indirection between clients and the real object.