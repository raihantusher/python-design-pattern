---
title: 'Memento Design pattern'

...
The Memento design pattern is used to capture and store the internal state of an object without exposing its internal structure, allowing the object to be restored to a previous state. It provides a way to maintain different versions (states) of an object and restore the object to a specific state when needed. This pattern is useful when you need to implement undo/redo functionality or save and restore the state of an object.

Here's an example of implementing the Memento pattern in Python:

```python
# Memento
class Memento:
    def __init__(self, state):
        self._state = state

    def get_state(self):
        return self._state

# Originator
class Editor:
    def __init__(self):
        self._content = ""

    def set_content(self, content):
        self._content = content

    def get_content(self):
        return self._content

    def create_memento(self):
        return Memento(self._content)

    def restore(self, memento):
        self._content = memento.get_state()

# Caretaker
class History:
    def __init__(self):
        self._mementos = []

    def push(self, memento):
        self._mementos.append(memento)

    def pop(self):
        return self._mementos.pop()

def main():
    editor = Editor()
    history = History()

    editor.set_content("Version 1")
    history.push(editor.create_memento())

    editor.set_content("Version 2")
    history.push(editor.create_memento())

    editor.set_content("Version 3")
    print("Current content:", editor.get_content())

    memento = history.pop()
    editor.restore(memento)
    print("Restored content:", editor.get_content())

if __name__ == "__main__":
    main()
```

In this example, we have the `Memento` class representing the memento, the `Editor` class as the originator, and the `History` class as the caretaker. The `Editor` class is responsible for creating mementos to capture its state and restoring its state from a memento. The `History` class maintains a stack of mementos to keep track of the history of the editor's state changes.

When the editor's content changes, it creates a memento and pushes it to the history. If a state needs to be restored, the editor can retrieve the desired memento from the history and restore its state.

By using the Memento pattern, you can implement features like undo/redo functionality, state persistence, or even version history tracking. This pattern is especially useful when you want to separate the responsibility of maintaining the state history from the object itself.