# Useful commands in python

## Filehandling, pickling, etc.

## String operations, Regexes, etc.

### Find all occurrences of a given substring in a string
```
import re
re.finditer(substring, string)
```

## Sorting, datastructures, etc.

### Sort a list in Python
```
list.sort(reverse=True|False, key=func)
```
func is a callback, often a lambda expression :
```
list.sort(reverse=True, key = lambda list_element: list_element[1]) # in a list of tuples, sort ascendingly, using the second value of each tuple as key 
```
**Note**: Sorting happens **in-place**


## Collections

### Counter
Returns a dictionary giving each element of a list as key and the number of times that element appears as a value.

```
from collections import Counter
dummy = ['A','A','B']
from collections import Counter
counter = Counter(dummy)
print(counter)
Counter({'A': 2, 'B': 1})
```

Note that min and max operation on Counter are applied to the counter keys

```
print(max(counter))
print(min(counter))
B
A
```

unless an explicit func for the key is supplied

```
print(max(counter, key=counter.get))
print(min(counter, key=counter.get))
A
B
```

## Map, Reduce and Filter

### Reduce
```
from functools import reduce
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])


```
