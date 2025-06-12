 Useful commands in python

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

### Argsort a numpy array
```
sort_idcs = np.argsort(similarity.tolist())
```

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

## Defaultdict
Very handy to avoid having to initialize lists separately when using them as values in a dictionary.
```
from collections import Defaultdict
s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4), ('red', 1)]
d = defaultdict(list)
for k, v in s:
     d[k].append(v)

sorted(d.items())
[('blue', [2, 4]), ('red', [1]), ('yellow', [1, 3])]
```

For nested defaultdicts do
```
d = defaultdict(lambda: defaultdict(list))
```

## Map, Filter and Reduce

### Map

```
items = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, items))
```

### Filter

```
number_list = range(-5, 5)
less_than_zero = list(filter(lambda x: x < 0, number_list))
print(less_than_zero)
```

### Reduce

```
from functools import reduce
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])
```

## Other neat tools
### tqdm for progress bars
```
from tqdm import tqdm

for element in tqdm(list):
    ## Do some stuff here with element
```
## Pathlib
#### Create dir if it doesn't exist yet
```
from pathlib import Path
Path('stampscollection/monte_carlo/').mkdir(parents=True, exist_ok=True)
```

## Iterators

### Elegant way to increment a global counter
```
import itertools

global_counter1 = itertools.count()

next(global_counter1)
```

## Assertions and exception handling
### Assertions
```
assert number > 0, f"number greater than 0 expected, got: {number}"
```

## Shell Interface
### Set Environment Variable
```
import os

os.environ["CUDA_DEVICE_ORDER"] = "PCI_BUS_ID"
os.environ["CUDA_VISIBLE_DEVICES"] = "1,2,3"
rank = int(os.environ["RANK"])
device = torch.device(f"cuda:{rank}")
```

## Type hints
Starting at Python3.5, are just annotations to be enforced by external tools or IDEs.

```
from typing import List, Set, Dict, Tuple

def generateLineString(self, current_line: List[str], maxWidth: int, is_last: bool = False):
""" This function implements etc.etc.
"""
```
[Great cheatsheet detailing type hints in Python](https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html)

