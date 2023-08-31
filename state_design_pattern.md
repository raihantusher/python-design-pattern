---
title: 'State design pattern'
...
The State design pattern is used to allow an object to change its behavior when its internal state changes. It allows an object to appear as if it has changed its class based on its current state, without changing the class itself. This pattern is useful when you have an object that can be in multiple states and its behavior needs to vary based on its current state.

Here's an example of implementing the State pattern in Python:

```python
# State interface
class State:
    def do_action(self, context):
        pass

# Concrete states
class StateA(State):
    def do_action(self, context):
        print("State A: Performing action and transitioning to State B")
        context.set_state(StateB())

class StateB(State):
    def do_action(self, context):
        print("State B: Performing action and transitioning to State A")
        context.set_state(StateA())

# Context
class Context:
    def __init__(self):
        self._state = StateA()

    def set_state(self, state):
        self._state = state

    def do_action(self):
        self._state.do_action(self)

def main():
    context = Context()

    context.do_action()
    context.do_action()
    context.do_action()

if __name__ == "__main__":
    main()
```

In this example, we have a `State` interface representing the states, and two concrete state classes `StateA` and `StateB`. The `Context` class represents the object whose behavior changes based on its state.

Each concrete state class (`StateA` and `StateB`) defines its behavior in the `do_action` method and may transition to a different state. The `Context` class contains a reference to the current state and delegates the `do_action` call to the current state.

By using the State pattern, you can encapsulate the behavior of an object in separate state classes, making it easier to manage and maintain different states and their corresponding behaviors. This pattern is particularly useful when you have a complex object that exhibits different behaviors based on its state and the behavior changes dynamically over time.