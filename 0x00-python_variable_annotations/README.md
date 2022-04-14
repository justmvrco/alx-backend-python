# 0x00. Python - Variable Annotations

## Resources
Read or watch:

* [Python 3 typing documentation](https://docs.python.org/3/library/typing.html)
* [MyPy cheat sheet](https://mypy.readthedocs.io/en/latest/cheat_sheet_py3.html)

## General
- How to validate your code with `mypy`

## Tasks

## [0. Basic annotations - add](./0-add.py)
Write a type-annotated function `add` that takes a float `a` and a float `b` as arguments and returns their sum as a float.
```
$ ./0-main.py
True
{'a':  <class 'float'>, 'b': <class 'float'>, 'return': <class 'float'>}
```

## [1. Basic annotations - concat](./1-concat.py)
Write a type-annotated function `concat` that takes a string `str1` and a string `str2` as arguments and returns a concatenated string
```
$ ./1-main.py
True
{'str1': <class 'str'>, 'str2': <class 'str'>, 'return': <class 'str'>}
```

## [2. Basic annotations - floor](./2-floor.py)
Write a type-annotated function `floor` which takes a float `n` as argument and returns the floor of the float.
```
$ ./2-main.py
True
{'n': <class 'float'>, 'return': <class 'int'>}
floor(3.14) returns 3, which is a <class 'int'>
```

## [3. Basic annotations - to string](./3-to_str.py)
Write a type-annotated function `to_str` that takes a float `n` as argument and returns the string representation of the float.
```
$ ./3-main.py
True
{'n': <class 'float'>, 'return': <class 'str'>}
to_str(3.14) returns 3.14, which is a <class 'str'>
```

## [4. Define variables](./4-define_variables.py)
Define and annotate the following variables with the specified values:

* `a`, an integer with a value of 1
* `pi`, a float with a value of 3.14
* `i_understand_annotations`, a boolean with a value of True
* `school`, a string with a value of “Holberton”
```
$ ./4-main.py
a is a <class 'int'> with a value of 1
pi is a <class 'float'> with a value of 3.14
i_understand_annotations is a <class 'bool'> with a value of True
school is a <class 'str'> with a value of Holberton
```

## [5. Complex types - list of floats](./5-sum_list.py)
Write a type-annotated function `sum_list` which takes a list `input_list` of floats as argument and returns their sum as a float.
```
$ ./5-main.py
True
{'input_list': typing.List[float], 'return': <class 'float'>}
sum_list(floats) returns 6.470000000000001 which is a <class 'float'>
```

## [6. Complex types - mixed list](./6-sum_mixed_list.py)
Write a type-annotated function `sum_mixed_list` which takes a list `mxd_lst` of integers and floats and returns their sum as a float.
```
$ ./6-main.py
{'mxd_lst': typing.List[typing.Union[int, float]], 'return': <class 'float'>}
True
sum_mixed_list(mixed) returns 679.13 which is a <class 'float'>
```

## [7. Complex types - string and int/float to tuple](./7-to_kv.py)
Write a type-annotated function `to_kv` that takes a string `k` and an int OR float `v` as arguments and returns a tuple. The first element of the tuple is the string `k`. The second element is the square of the int/float `v` and should be annotated as a float.
```
$ ./7-main.py
{'k': <class 'str'>, 'v': typing.Union[int, float], 'return': typing.Tuple[str, float]}
('eggs', 9)
('school', 0.0004)
```

## [8. Complex types - functions](./8-make_multiplier.py)
Write a type-annotated function `make_multiplier` that takes a float `multiplier` as argument and returns a function that multiplies a float by `multiplier`.
```
$ ./8-main.py
{'multiplier': <class 'float'>, 'return': typing.Callable[[float], float]}
4.928400000000001
```

## [9. Let's duck type an iterable object](./9-element_length.py)
Annotate the below function’s parameters and return values with the appropriate types
```
def element_length(lst):
    return [(i, len(i)) for i in lst]
$ ./9-main.py 
{'lst': typing.Iterable[typing.Sequence], 'return': typing.List[typing.Tuple[typing.Sequence, int]]}
```

## [10. Duck typing - first element of a sequence](./100-safe_first_element.py)
Augment the following code with the correct duck-typed annotations:

```
# The types of the elements of the input are not know
def safe_first_element(lst):
    if lst:
        return lst[0]
    else:
        return None
$ ./100-main.py 
{'lst': typing.Sequence[typing.Any], 'return': typing.Union[typing.Any, NoneType]}
```

## [11. More involved type annotations](./101-safely_get_value.py)
Given the parameters and the return values, add type annotations to the function

Hint: look into `TypeVar`
```
def safely_get_value(dct, key, default = None):
    if key in dct:
        return dct[key]
    else:
        return default
$ ./101-main.py 
Here's what the mappings should look like
dct: typing.Mapping
key: typing.Any
default: typing.Union[~T, NoneType]
return: typing.Union[typing.Any, ~T]
```

## [12. Type Checking](./102-type_checking.py)
Use `mypy` to validate the following piece of code and apply any necessary changes.

```
def zoom_array(lst: Tuple, factor: int = 2) -> Tuple:
    zoomed_in: Tuple = [
        item for item in lst
        for i in range(factor)
    ]
    return zoomed_in


array = [12, 72, 91]

zoom_2x = zoom_array(array)

zoom_3x = zoom_array(array, 3.0)
$ mypy 102-type_checking.py
Success: no issues found in 1 source file
$ ./102-main.py 
{'lst': typing.Tuple, 'factor': <class 'int'>, 'return': typing.List}
```
