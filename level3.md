# Python Functions 
functions are independent block of code that can be called from anywhere in the program.
functions are defined using the keyword def followed by the function name and parentheses ().
and the function body is indented.

function are created to perform a specific task.

### Types of functions
1. Built-in functions
2. User-defined functions

### Built-in functions
These are functions that are already defined in python and can be used directly.
Examples are:
1. print()
2. input()
3. len()
4. range()
5. type()

### User-defined functions
These are functions that are created by the programmer to perform a specific task.
#### Syntax
```python
def function_name():
    function body
```
#### Example
```python
def add():
    a = 10
    b = 20
    c = a + b
    print(c)
```
#### Calling a function
```python
add()
```
#### Passing arguments to a function
```python
def add(a, b):
    c = a + b
    print(c)
```
#### Calling a function
```python
add(10, 20)
```
#### Return statement
```python
def add(a, b):
    c = a + b
    return c
```
#### Calling a function
```python
result = add(10, 20)
print(result)
```
#### Default arguments
```python
def add(a, b=10):
    c = a + b
    return c
```
#### Calling a function
```python

result = add(10)
print(result)
```
 #### args and kwargs
 
 args and kwargs are used to pass a variable number of arguments to a function.
args is used to pass a variable number of non-keyworded arguments.
args is a tuple of arguments.

kwargs is used to pass a variable number of keyworded arguments.
kwargs is a dictionary of arguments.

*args and **kwargs are used when we are not sure of the number of arguments to pass to a function.
*example*
```python
def add(*args):
    print(args)
    print(type(args))
    result = 0
    for i in args:
        result += i
    return result
```
#### Calling a function
```python
result = add(10, 20, 30, 40, 50)
print(result)
```
#### kwargs
```python
def add(**kwargs):
    print(kwargs)
    print(type(kwargs))
    result = 0
    for i in kwargs.values():
        result += i
    return result
```
#### Calling a function
```python
result = add(a=10, b=20, c=30, d=40, e=50)
print(result)
```
#### args and kwargs
```python
def add(*args, **kwargs):
    print(args)
    print(kwargs)
    result = 0
    for i in kwargs.values():
        result += i
    for i in args:
        result += i
    return result
```

#### Calling a function
```python
result = add(10, 20, 30, 40, 50, a=10, b=20, c=30, d=40, e=50)
print(result)
```
#### Lambda functions
Lambda functions are anonymous functions that are defined without a name.
Lambda functions are defined using the keyword lambda followed by the arguments and a colon.
#### Syntax
```python
lambda arguments: expression
```
#### Example
```python
add = lambda a, b: a + b
print(add(10, 20))
```
#### Map function
The map function is used to apply a function to a list of elements.
#### Syntax
```python
map(function, iterable)
```
#### Example
```python
def add(a):
    return a + 10
result = list(map(add, [10, 20, 30, 40, 50]))
print(result)
*output*
[20, 30, 40, 50, 60]
```

# Excersise
1. Write a function that takes a number as an argument and returns the square of the number.
2. Write a function that takes a Array of number and returns the sum of the numbers.
3. Write a function that takes a Array of number and returns the largest among them.
4. Write a program to implement binary search in python .
5. Write a program to implement quick sort in python . 
6. Write a program that accepts aribitary number of arguments and  returns the sum of the arguments.