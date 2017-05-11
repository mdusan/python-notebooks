
# Multiples of 3 and 5
>If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6
and 9. The sum of these multiples is 23.
>
>Find the sum of all the multiples of 3 or 5 below 1000.

_________

### Solution 1
This algorithm iterates through the list of all natural numbers up to the maximum value **`target`** and, using the **`reduce()`** function, during the iteration calculates the sum of all multiples of a given number $n$ in the range.

This "pythonic" way of iteration and immediate reduction of a range (a list) of values to the sum of appropriate values is probably more efficient than any other algorithm involving iteration.

However, the efficiency of this algorithm is not the otimal one. For big target numbers calculation takes a long time using a singe 64-bit processor and enough primary memory. For example, for all natural numbers below 100'000'000 it takes a Mac OS X 64-bit Intel machine 128 seconds to calculate the three sums (see the output below). As the efficiency of this algorithm is approximately $O(n)$, for calculating sums of appropriate numbers below the next order of magnitude (1'000'000'000) the calculation time would be expected in the order of magnitude of hours.


```python
def SumDivisibleBy(n, target):
    return reduce(lambda x, y : x + y, [x for x in range(target) if x % n == 0])

import time
target = int(raw_input("Enter maximum natural number: "))
start_time=time.time()
print SumDivisibleBy(3, target) + SumDivisibleBy(5, target) - SumDivisibleBy(15, target)
print str(time.time()-start_time) + " seconds"
```

    Enter maximum natural number: 100000000
    2333333316666668
    128.546073914 seconds


____
### Solution 2
There is a smarter solution if we use a bit of mathematics. The sum of all numbers divisible by a given number $n$ is:

\begin{equation*}
n + 2n + 3n + 4n + \cdots + pn \text{, where } p = \frac{target}{n} \text{ is rounded down to nearest integer}  
\end{equation*}
\begin{equation*}
n + 2n + 3n + 4n + \cdots + pn = n (1 + 2 + 3 + 4 + \cdots. + p) = n\sum_{i=1}^{p}i = n \frac{p (p+1)}{2}
\end{equation*}

The efficiency of this algorithm is optimal. For example, for all natural numbers below 100'000'000 it takes a Mac OS X 64-bit Intel machine 5 nanoseconds to calculate the three sums (see the output below). Compare this with the time of 128 seconds in the example above. As the efficiency of this algorithm is $O(1)$, for calculating sums of appropriate numbers below the next order of magnitude (1'000'000'000) the calculation time would remain unchanged.


```python
def SumDivisibleBy(n, target):
    p = target // n
    return n * (p * (p + 1) / 2)

import time
target = int(raw_input("Enter maximum natural number: "))
start_time=time.time()
print SumDivisibleBy(3, target) + SumDivisibleBy(5, target) - SumDivisibleBy(15, target)
print str(time.time()-start_time) + " seconds"
```

    Enter maximum natural number: 100000000
    2333333416666668
    0.000525951385498 seconds

