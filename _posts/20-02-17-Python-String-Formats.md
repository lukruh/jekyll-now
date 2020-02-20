---
layout: post
title: python3 string formats
---

Formating strings is the way to go, when data of any type is used in text. Very common applications are logging values of variables, text output or formatting data in a specific format like how many digit a number has, showing leading `+` or `0`,  provide a date in `yy-mm-dd` and so on. In python3.6 (or newer), are three different ways to do this. They are shown with all options and some examples in the following. 
To format more complex thinks, like documents or websites, jinja templates can be used.

## % format

```python
>>> name = 'Joe'
>>> age = 30
>>> weight = 80.52
>>> print('I am %s, %d years old and %.1f kg heavy.' %(name, age, weight))
I am Joe, 30 years old and 80.5 kg heavy.
```

## str.format()

```python
>>> name = 'Joe'
>>> age = 30
>>> weight = 80.52
>>> print(f'I am {}, {} years old and {:.1f} kg heavy.'.format(name, age, weight))
I am Joe, 30 years old and 80.5 kg heavy.
```

It can be useful to unpack a dictionary instead of passing the variables to the `.format()` method, if the format strings are defined somewhere else or the data is available in a `dict` already. The keys can be placed in the curly brackets `{ }`  to ensure the order is correct.

```python
>>> person = {'name': 'Joe', 'age': 30, 'weight': 80.52}
>>> template = 'I am {name}, {age} years old and {weight:.1f} kg heavy.'
>>> print(template.format(**person))
I am Joe, 30 years old and 80.5 kg heavy.
```

The unpacking operator `**` in front of the dictionary is required, to make sure that the variables from the contained in the ditionary `person` are passed as singular variables, and not as one object. `some_function(**person)` is the same as  `some_function(name='Joe', age=30, weight=80.52)`.



## fstring

```python
>>> name = 'Joe'
>>> age = 30
>>> weight = 80.52
>>> print(f'I am {name}, {age} years old and {weight:.1f} kg heavy.')
I am Joe, 30 years old and 80.5 kg heavy.
```



## Format keys