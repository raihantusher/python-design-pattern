---
title: 'Mediator design pattern'
...

The Mediator design pattern is used to reduce direct dependencies between objects by introducing a mediator object that centralizes communication and coordination between these objects. It promotes loose coupling among components by facilitating indirect communication between them through the mediator. This pattern is particularly useful when you have a set of objects that need to interact in complex ways without being tightly coupled.

Here's an example of implementing the Mediator pattern in Python:

```python
# Mediator
class ChatMediator:
    def send_message(self, message, user):
        pass

# Concrete Mediator
class ConcreteChatMediator(ChatMediator):
    def __init__(self):
        self.users = []

    def add_user(self, user):
        self.users.append(user)

    def send_message(self, message, user):
        for u in self.users:
            if u != user:
                u.receive(message)

# Colleague
class User:
    def __init__(self, name, mediator):
        self.name = name
        self.mediator = mediator

    def send(self, message):
        self.mediator.send_message(message, self)

    def receive(self, message):
        print(f"{self.name} received: {message}")

def main():
    mediator = ConcreteChatMediator()

    user1 = User("Alice", mediator)
    user2 = User("Bob", mediator)
    user3 = User("Charlie", mediator)

    mediator.add_user(user1)
    mediator.add_user(user2)
    mediator.add_user(user3)

    user1.send("Hello, everyone!")
    user2.send("Hi, Alice!")

if __name__ == "__main__":
    main()
```

In this example, we have a `ChatMediator` interface representing the mediator, a concrete mediator `ConcreteChatMediator`, and a `User` class representing the colleagues. The mediator's `send_message` method facilitates communication between users.

When a user sends a message, the mediator distributes the message to other users, allowing indirect communication. This way, the users are not directly aware of each other, reducing the coupling between them.

By using the Mediator pattern, you can promote a more organized and controlled communication between components, particularly when the interactions between components become complex. This pattern is useful for scenarios where a set of objects need to interact in a way that avoids tight coupling and simplifies their individual responsibilities.