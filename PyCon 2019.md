# Reuven M. Lerner - Practical decorators - PyCon 2019

## Let's decorate a function 
- See this:
```python
@mydeco
def add(a, b):
    return a + b
```

- Think this:
```python
def add(a, b):
    return a + b
add = mydeco(add)
```

Three callables! (add, @mydeco, the return value frrom mydeco(add) assigned back to add.

## Defining a Decorator
```python
def mydeco(func):       # executes once, when we decorate the function
    def wrapper(*args, **kwargs):       # executes each time the decorated function runs
        return f'{func(*args, **kwargs)}!!!'
    return wrapper
```

5:31
