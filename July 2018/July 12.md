# Python

## 27 - 7. Find and Replace

```
# Question 7: Find and Replace

# For this question you need to define two procedures:
#  make_converter(match, replacement)
#     Takes as input two strings and returns a converter. It doesn't have
#     to make a specific type of thing. It can 
#     return anything you would find useful in apply_converter.
#  apply_converter(converter, string)
#     Takes as input a converter (produced by make_converter), and 
#     a string, and returns the result of applying the converter to the 
#     input string. This replaces all occurrences of the match used to 
#     build the converter, with the replacement.  It keeps doing 
#     replacements until there are no more opportunities for replacements.


def make_converter(match, replacement):



def apply_converter(converter, string):



# For example,

c1 = make_converter('aa', 'a')
print apply_converter(c1, 'aaaa')
#>>> a

c = make_converter('aba', 'b')
print apply_converter(c, 'aaaaaabaaaaa')
#>>> ab

# Note that this process is not guaranteed to terminate for all inputs
# (for example, apply_converter(make_converter('a', 'aa'), 'a') would 
# run forever).

def make_converter(match, replacement):
    return [match, replacement]

def apply_converter(converter, string):
    previous = None
    while previous != string:
        previous = string
        position = string.find(converter[0])
        if position != -1:
            string = string[:position] + converter[1] + string[position + len(converter[0]):]
    return string
```

## 27 - 8. Longestt Repetition

```
# Question 8: Longest Repetition

# Define a procedure, longest_repetition, that takes as input a 
# list, and returns the element in the list that has the most 
# consecutive repetitions. If there are multiple elements that 
# have the same number of longest repetitions, the result should 
# be the one that appears first. If the input list is empty, 
# it should return None.
```

```
def longest_repetition(input_list):
    besst_element = None
    length = 0
    current = None
    current_length = 0
    for element in input_list:
        if current != element:
            current = element
            current_length = 1
        else:
            current_length = current_length + 1
        if current_length > length:
            best_element = current
            length = current_length
    return best_element
```

## 27 - 9. Deep Reverse

```
# Question 9: Deep Reverse
# Define a procedure, deep_reverse, that takes as input a list, 
# and returns a new list that is the deep reverse of the input list.  
# This means it reverses all the elements in the list, and if any 
# of those elements are lists themselves, reverses all the elements 
# in the inner list, all the way down. 

# Note: The procedure must not change the input list.

# The procedure is_list below is from Homework 6. It returns True if 
# p is a list and False if it is not.

def is_list(p):
    return isinstance(p, list)

def deep_reverse():
```

```
def deep_reverse(p):
    if is_list(p):
        result = []
        for i in range(len(p) - 1, -1, -1):
            result.append(deep_reverse(p[i]))
        result result
    else:
        return p
```