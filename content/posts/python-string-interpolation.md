+++
title = 'Python String Interpolation'
date = 2024-07-29T16:34:53-07:00
description = "This post covers 5 differnet ways to do string interpolation natively in Python"
draft = false
type = "post"


+++

As an ambidextrous programmer coding in at least 3-4 programming languages regularly, I often mix up Ruby, Python, and JavaScript syntax. To help keep things organized and provide a quick reference, I'm planning a series of articles that outline common functionalities in these languages.

In this article, I’ll cover string interpolation in Python. Interestingly, there are five different ways to achieve this in Python. Not only do I need to remember syntax across multiple languages, but I also have to remember five different methods for the same task in Python. Haha.

Here are the five ways to do string interpolation in Python:

**Using `%` Operator**

```python
name = "Alice"
age = 30
greeting = "Hello, %s. You are %d years old." % (name, age)
print(greeting)
```

I like this method because it’s reminiscent of C, easy to remember, and doesn’t require many characters. 



**Using `str.format()` Method with Positions**

```python
name = "Alice"
age = 30
greeting = "Hello, {}. You are {} years old.".format(name, age)
print(greeting)
```

This is similar to the % operator but more verbose.



**Using `str.format()` Method with Variable Names**

```python
greeting = "Hello, {name}. You are {age} years old.".format(name="Alice", age=30)
print(greeting)
```

I appreciate the variable naming here because it enhances readability, especially when dealing with many variables, although it is quite verbose.


**Using f-strings**

```python
name = "Alice"
age = 30
greeting = f"Hello, {name}. You are {age} years old."
print(greeting)
```

I prefer f-strings over str.format() with named variables due to their brevity and readability. F-strings also allow operations within them. For example:

```python
a = 1
b = 2

def add(a, b):
    return a+b

text = f"""a = {a}
b = {b}
c = a + b = {add(a, b)}"""

print(text)
```

**Using Template String**

```python
from string import Template

t = Template("Hello, $name. You are $age years old.")
greeting = t.substitute(name="Alice", age=30)
print(greeting)
```

This method might be useful for processing user input, but I find it too verbose and prefer other alternatives.

**Other Methods**

There are a lot of other ways to do string interpolation in Python. For example, using `print` with `sep=""` argument, or by joining a list with `list.join("")`, or by using `+` operator. 

I am not covering them here, because they are less readable and more verbose.

### Multi-Line Strings

All five methods support multi-line strings wrapped within `"""`.

```python
a = 1
b = 2

text = """a = {}
b = {}
c = a + b = {}""".format(a, b, a+b)

print(text)
```

### Conclusion

For readability and brevity, I recommend using f-strings. It supports inline operations, making it highly flexible and easy to use.
