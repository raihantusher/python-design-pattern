---
title:'Chain of Responsibility design pattern'
...
The Chain of Responsibility design pattern is used to create a chain of objects, where each object in the chain has the ability to process a request and optionally pass the request to the next object in the chain. This pattern allows you to decouple the sender and receiver of a request and provides a way to handle the request in a flexible and dynamic manner.

Here's an example of implementing the Chain of Responsibility pattern in Python:

```python
# Handler interface
class Handler:
    def set_successor(self, successor):
        pass

    def handle_request(self, request):
        pass

# Concrete handlers
class ConcreteHandler1(Handler):
    def set_successor(self, successor):
        self.successor = successor

    def handle_request(self, request):
        if request == "Request1":
            print("ConcreteHandler1 handling the request")
        else:
            if self.successor is not None:
                self.successor.handle_request(request)

class ConcreteHandler2(Handler):
    def set_successor(self, successor):
        self.successor = successor

    def handle_request(self, request):
        if request == "Request2":
            print("ConcreteHandler2 handling the request")
        else:
            if self.successor is not None:
                self.successor.handle_request(request)

class ConcreteHandler3(Handler):
    def set_successor(self, successor):
        self.successor = successor

    def handle_request(self, request):
        if request == "Request3":
            print("ConcreteHandler3 handling the request")
        else:
            if self.successor is not None:
                self.successor.handle_request(request)

def main():
    handler1 = ConcreteHandler1()
    handler2 = ConcreteHandler2()
    handler3 = ConcreteHandler3()

    handler1.set_successor(handler2)
    handler2.set_successor(handler3)

    handler1.handle_request("Request1")
    handler1.handle_request("Request2")
    handler1.handle_request("Request3")
    handler1.handle_request("UnknownRequest")

if __name__ == "__main__":
    main()
```

In this example, we have a `Handler` interface representing the handler in the chain. The `ConcreteHandler1`, `ConcreteHandler2`, and `ConcreteHandler3` classes are the concrete handlers that can process requests or pass them to the next handler in the chain.

Each concrete handler has a `set_successor` method to set the next handler in the chain and a `handle_request` method to process requests. If a handler cannot handle a request, it passes the request to its successor.

By using the Chain of Responsibility pattern, you can create a dynamic and flexible chain of handlers to process requests based on their capabilities. This pattern is useful when you have multiple objects that can handle a request in different ways, and you want to avoid tight coupling between the sender and receiver of the request.