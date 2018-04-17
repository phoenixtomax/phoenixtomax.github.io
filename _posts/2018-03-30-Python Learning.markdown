# Python Learning

> The modification of this post is still ongoing.

## Class

### init, open, new, del and exit
```python
class Vehicle:
    def __init__(self):
        print "Vehicle init"
        pass

    def __open__(self):
        print "Vehicle open"
        pass

    def __new__(cls, *args, **kwargs):
        print "Vehicle new"
        return super(Vehicle, cls).__new__(cls)

    def __enter__(self):
        print "Vehicle enter"
        pass

    def __del__(self):
        print "Vehicle delete"
        pass

    def __exit__(self, exc_type, exc_val, exc_tb):
        print "Vehicle exit"
        pass

Vehicle()

if __name__ == "__main__":

    v = Vehicle()

    with Vehicle() as vv:
       pass
```
Outputs:
> Vehicle init
> Vehicle delete
> Vehicle init
> Vehicle init
> Vehicle enter
> Vehicle exit
> Vehicle delete
> Vehicle delete

## Iteration

### enumeration
```python
my_list = ['apple', 'banana', 'grapes', 'pear']
>>> for c, value in enumerate(my_list, 2): print(c, value)
... 
(2, 'apple')
(3, 'banana')
(4, 'grapes')
(5, 'pear')
>>> for c, value in enumerate(my_list, -1): print(c, value)
... 
(-1, 'apple')
(0, 'banana')
(1, 'grapes')
(2, 'pear')
```

Enumerate elements with specified index *2*, *-1*.

### Generator
```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
```
```python
>>> f = fib(6)
>>> f
<generator object fib at 0x104feaaa0>
```

### Yield
```python
def odd():
    print('step 1')
    yield 1
    print('step 2')
    yield(3)
    print('step 3')
    yield(5)
```
```python
>>> o = odd()
>>> next(o)
step 1
1
>>> next(o)
step 2
3
>>> next(o)
step 3
5
>>> next(o)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

## Filter
```python
def is_palindrome(n):
    n=str(n)
    m=n[::-1]
    return n==m

output = filter(is_palindrome, range(1, 1000))
print('1~1000:', list(output))
if list(filter(is_palindrome, range(1, 200))) == [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 22, 33, 44, 55, 66, 77, 88, 99, 101, 111, 121, 131, 141, 151, 161, 171, 181, 191]:
    print('测试成功!')
else:
    print('测试失败!')
```
