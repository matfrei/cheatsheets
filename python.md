# Useful commands in python

## Filehandling, pickling, etc.

## Sorting, datastructures, etc.

### Sort a list in Python
```
list.sort(reverse=True|False, key=func)
```
func is a callback, often a lambda expression :
```
list.sort(reverse=True, key = lambda list_element: list_element[1]) # in a list of tuples, sort ascendingly, using the second value of each tuple as key 
```
