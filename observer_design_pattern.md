---
title: 'Observer design pattern'
...
The Observer design pattern is used to establish a one-to-many dependency between objects, so that when one object (the subject) changes its state, all its dependent objects (observers) are notified and updated automatically. This pattern is often used to implement event handling systems and is crucial in achieving loose coupling between components.

Here's an example of implementing the Observer pattern in Python:

```python
# Observer interface
class Observer:
    def update(self, message):
        pass

# Subject
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def notify(self, message):
        for observer in self._observers:
            observer.update(message)

# Concrete observer
class ConcreteObserver(Observer):
    def __init__(self, name):
        self.name = name

    def update(self, message):
        print(f"{self.name} received message: {message}")

def main():
    subject = Subject()

    observer1 = ConcreteObserver("Observer 1")
    observer2 = ConcreteObserver("Observer 2")
    observer3 = ConcreteObserver("Observer 3")

    subject.attach(observer1)
    subject.attach(observer2)
    subject.attach(observer3)

    subject.notify("Hello, observers!")

if __name__ == "__main__":
    main()
```

In this example, we have the `Observer` interface representing the observer, the `Subject` class as the subject, and the `ConcreteObserver` class as the concrete observer. The `Subject` maintains a list of attached observers and notifies them when a change occurs.

Observers (`ConcreteObserver` instances) are attached to the subject using the `attach` method. When the subject's state changes, it calls the `notify` method to inform all attached observers. Each observer's `update` method is called with the updated information.

By using the Observer pattern, you can achieve a decoupled and flexible design where subjects and observers are loosely connected. This pattern is especially useful for implementing user interfaces, event-driven systems, and any scenario where changes in one object need to be propagated to multiple dependent objects.