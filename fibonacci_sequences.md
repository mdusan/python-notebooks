
Create a Fibonacci sequence of first `n` numbers, with seed values `[0, 1]`:


```python
def fibonacci_sequence(n):
    x = [0, 1]
    [x.append(x[-1] + x[-2]) for i in range(n - len(x))]
    return x
fibonacci_sequence(10)
```

_______
Create a Fibonacci sequence of first `n` numbers, with seed values `[1, 1]`:


```python
def fibonacci_sequence(n):
    x = [1, 1]
    [x.append(x[-1] + x[-2]) for i in range(n - len(x))]
    return x
fibonacci_sequence(15)
```

______
Create a Fibonacci sequence for all numbers ending with given `last` number: 


```python
def fibonacci_sequence(last):
    x = [0, 1]
    while x[-1] + x[-2] <= last:
        x.append(x[-1] + x[-2])
    return x
fibonacci_sequence(100)
```

_____
Create a Fibonacci sequence of numbers in the given range:


```python
def fibonacci_sequence(first, last):
    x = [0, 1]
    while (x[-1] + x[-2]) <= last:
        x.append(x[-1] + x[-2])
    return [x for x in x if x >= first]
fibonacci_sequence(10, 1000)
```

_______
Create a Fibonacci sequence for `n` numbers ending with given `last` number:


```python
def fibonacci_sequence(last, n):
    x = [0, 1]
    while (x[-1] + x[-2]) <= last:
        x.append(x[-1] + x[-2])
    return sorted([x[len(x)-1-i] for i in range(n)])
fibonacci_sequence(100, 5)
```

_______
Create a Fibonacci sequence of `n` numbers starting with given `first` number:


```python
def fibonacci_sequence(first, n):
    x = [0, 1]
    while (x[-1] + x[-2]) < first:
        x.append(x[-1] + x[-2])
    [x.append(x[-1] + x[-2]) for i in range(n)]
    return [x for x in x if x >= first]
fibonacci_sequence(20, 10)
```
