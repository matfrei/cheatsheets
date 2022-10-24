# Useful commands in python

## Filehandling, pickling, etc.

## Sorting, datastructures, etc.

### Sort a list in Python
```
list.sort(reverse=True|False, key=func)
```
func is a callback, often a lambda expression
```
lambda list_element: list_element[1] # in a list of tuples, use the second value of each tuple as key 
```
