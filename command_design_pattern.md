---
title: 'Command Design Pattern'
...

The Command design pattern is used to encapsulate a request as an object, thereby allowing for parameterization of clients with different requests, queuing of requests, and logging of requests. It decouples the sender and receiver of a command, allowing for more flexibility in how commands are executed and processed.

Here's an example of implementing the Command pattern in Python:

```python
# Command interface
class Command:
    def execute(self):
        pass

# Receiver
class Light:
    def turn_on(self):
        print("Light is on")

    def turn_off(self):
        print("Light is off")

# Concrete commands
class TurnOnCommand(Command):
    def __init__(self, light):
        self.light = light

    def execute(self):
        self.light.turn_on()

class TurnOffCommand(Command):
    def __init__(self, light):
        self.light = light

    def execute(self):
        self.light.turn_off()

# Invoker
class RemoteControl:
    def __init__(self):
        self.commands = {}

    def set_command(self, slot, command):
        self.commands[slot] = command

    def press_button(self, slot):
        if slot in self.commands:
            self.commands[slot].execute()

def main():
    remote_control = RemoteControl()
    light = Light()

    turn_on_command = TurnOnCommand(light)
    turn_off_command = TurnOffCommand(light)

    remote_control.set_command(0, turn_on_command)
    remote_control.set_command(1, turn_off_command)

    remote_control.press_button(0)  # Turns on the light
    remote_control.press_button(1)  # Turns off the light

if __name__ == "__main__":
    main()
```

In this example, we have a `Command` interface representing the command, and two concrete command classes `TurnOnCommand` and `TurnOffCommand` that implement the command interface. The `Light` class acts as the receiver, and the `RemoteControl` class acts as the invoker.

The client (in the `main` function) creates command objects and associates them with specific slots in the remote control. When the remote control's `press_button` method is called, it invokes the corresponding command's `execute` method.

By using the Command pattern, you can encapsulate and parameterize actions, making it easier to add new commands without modifying existing code. This pattern is useful when you want to separate the logic for issuing a command from the logic for executing the command, allowing for more flexibility in designing command-based systems.