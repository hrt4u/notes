
#### tags
#topic #wip


# Mutable and Immutable Data Types (Python)
<!-- TOPIC Definition goes here -->
>Python classifies its data types into mutable and immutable categories. Mutable data types can be modified after their creation, while immutable types cannot.

## Mutable Data Types:

> -   `list`
> -   `set`
> -   `dict`
> -   Custom classes (usually)

### Side effects with Mutable types

> Because mutable types can be altered after creation, they can lead to unintended side effects, especially when they're used as default arguments in functions or shared among different scopes. For example:

```python
def append_to(num, target=[]):
    target.append(num)
    return target

print(append_to(1))  # Outputs: [1]
print(append_to(2))  # Outputs: [1, 2], not [2] as some might expect
```

> Here, `target` is a mutable list. Because it's a default argument, it's created only once when the function is defined. So, the `append_to()` calls are modifying the same list.


## Immutable Data Types

> -   `int`
> -   `float`
> -   `bool`
> -   `str`
> -   `tuple`
> -   `frozenset`

> Once an object of an immutable type is created, its content cannot be changed.

### Hashing

Immutable types can be used as dictionary keys because their value does not change over time. This allows Python to create a unique hash value for each key which is used for quick access to dictionary values.

### Performance Python's Special Tricks

Python uses specific techniques to optimize the usage of immutable types, making it more memory efficient and faster.

#### String and Integer Pooling

Python uses a method called "interning". Interning is a technique where Python tries to use existing objects in memory rather than creating a new object every time.

In Python, **small integers (-5 to 256)** are interned, as these numbers are most commonly used.

For string interning, Python automatically applies it only to some strings: s**tring literals consisting only of ASCII letters, digits, or underscores**. This is done for performance optimization and memory usage, as such strings are often used in code (e.g., variable names, dictionary keys).

```python
a = "Hello, World!" 
b = "Hello, World!"
a is b # False

a = "abgrdsddsd"
b = "abgrdsddsd"
a is b # True

a = 32
b = 32
a is b # True

a = 300
b = 300
a is b # False
```

### Speed Dynamics

> Mutable objects are typically slower to read but quicker when it comes to writing and changing. On the other hand, it's the opposite for immutable objects: they're fast to read but slower to write to.

### Thread Interaction

When a program uses multithreading, immutable objects provide a guarantee: they won't be changed by another thread after they've been created. This can greatly simplify the development of multithreaded applications. It reduces the risks of race conditions and data synchronization problems.

---
### Internal Links
<!-- Links related notes -->
[[Python]]

### References
<!-- Links to pages not referenced in the content -->
##### Russian

##### English
