---
title: 'Strategy design pattern'

...
The Strategy design pattern is used to define a family of interchangeable algorithms or behaviors and make them available to a client object. It allows the client to choose and switch between different algorithms without changing the client's code. This pattern is useful when you have multiple ways of performing a task and want to provide flexibility in selecting the appropriate strategy.

Here's an example of implementing the Strategy pattern in Python:

```python
# Strategy interface
class PaymentStrategy:
    def pay(self, amount):
        pass

# Concrete strategies
class CreditCardPayment(PaymentStrategy):
    def __init__(self, card_number, expiration_date):
        self.card_number = card_number
        self.expiration_date = expiration_date

    def pay(self, amount):
        print(f"Paying ${amount} with credit card {self.card_number}")

class PayPalPayment(PaymentStrategy):
    def __init__(self, email):
        self.email = email

    def pay(self, amount):
        print(f"Paying ${amount} via PayPal to {self.email}")

# Context
class ShoppingCart:
    def __init__(self, payment_strategy):
        self.items = []
        self.payment_strategy = payment_strategy

    def add_item(self, item):
        self.items.append(item)

    def calculate_total(self):
        total = sum(item.price for item in self.items)
        return total

    def checkout(self):
        total = self.calculate_total()
        self.payment_strategy.pay(total)

def main():
    credit_card = CreditCardPayment("1234-5678-9012-3456", "12/25")
    paypal = PayPalPayment("user@example.com")

    cart1 = ShoppingCart(credit_card)
    cart1.add_item(Item("Item 1", 50))
    cart1.add_item(Item("Item 2", 30))
    cart1.checkout()

    cart2 = ShoppingCart(paypal)
    cart2.add_item(Item("Item 3", 25))
    cart2.add_item(Item("Item 4", 40))
    cart2.checkout()

class Item:
    def __init__(self, name, price):
        self.name = name
        self.price = price

if __name__ == "__main__":
    main()
```

In this example, we have a `PaymentStrategy` interface representing the strategy, and two concrete strategy classes `CreditCardPayment` and `PayPalPayment`. The `ShoppingCart` class represents the context, which is the client object that uses a selected payment strategy to perform the payment.

The `ShoppingCart` class contains a reference to a payment strategy and uses it to perform the payment based on the chosen strategy. This allows the client to switch between different payment strategies without changing the `ShoppingCart` code.

By using the Strategy pattern, you can encapsulate different behaviors (payment methods in this case) as separate strategies, making it easy to add new strategies and switch between them. This pattern is especially useful when you want to avoid code duplication and provide a way for clients to select different algorithms or behaviors dynamically.