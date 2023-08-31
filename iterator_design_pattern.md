---
title: 'Iterator Design Pattern'
...
The Iterator design pattern is used to provide a way to access elements of a collection (such as a list or an array) sequentially without exposing the underlying implementation details. It involves creating an iterator object that encapsulates the traversal of the collection, allowing clients to iterate over the collection's elements using a common interface.

In Python, the Iterator pattern is already supported through built-in features like iterators and iterables. Here's an example of using the Iterator pattern with Python's built-in iterator and iterable features:

```python
# Iterable
class MyCollection:
    def __init__(self):
        self._data = []

    def add_item(self, item):
        self._data.append(item)

    def __iter__(self):
        return MyIterator(self._data)

# Iterator
class MyIterator:
    def __init__(self, data):
        self._data = data
        self._index = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self._index < len(self._data):
            value = self._data[self._index]
            self._index += 1
            return value
        raise StopIteration

def main():
    collection = MyCollection()
    collection.add_item("Item 1")
    collection.add_item("Item 2")
    collection.add_item("Item 3")

    for item in collection:
        print(item)

if __name__ == "__main__":
    main()
```

In this example, we have the `MyCollection` class representing the iterable collection and the `MyIterator` class representing the iterator. The `MyCollection` class defines the `__iter__` method to create and return an instance of the iterator class. The `MyIterator` class implements the `__next__` method to traverse through the collection's elements.

When the `for` loop is used to iterate over the `MyCollection` object, it internally uses the `MyIterator` object to traverse and access each element of the collection.

Python's built-in iterator protocol (`__iter__` and `__next__` methods) simplifies the implementation of the Iterator pattern, making it straightforward to create custom iterators and iterables for your own collections.