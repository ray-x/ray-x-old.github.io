---
layout: post
title: "Python Fundamental"
author: "Ray"
header-style: text
tags:
    - backend
    - python
---

# Fundamental of Python, a Jump start

# [Python Cheat Sheet for Leetcode - LeetCode Discuss](https://leetcode.com/discuss/study-guide/2122306/Python-Cheat-Sheet-for-Leetcode)

# Create a list with size: {#create-a-list-with-size collapsed="true"}

## python

``` python
[None] * 10
[] * 10 #THIS WONT WORK
list(range(10))  # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[{}] * 3
[[]] * 3

```

# Sort/Heap [Sorting HOW TO](https://docs.python.org/3/howto/sorting.html) {#sortheap-sorting-how-to collapsed="true"}

## Note: sorted() will return a sorted list, it not change the original one

while list.sort() will change the original list

# Key Func: {#key-func collapsed="true"}

## a func to be called on each list elem, e.g. key=str.lower

## it can be a lambda, e.g. key = lambda student: student.first\_ name

## The Key Functions are used in {{embed ((64a3827c-147d-443e-bb06-6b0e9f3ef2e0)) }}

# operator \`\*from\* **operator** **import** itemgetter, attrgetter\` {#operator-from-operator-import-itemgetter-attrgetter collapsed="true"}

## 2nd and then 3rd element in tuple/list: \`sorted(student~tuples~, key=itemgetter(2, 3))\`

-   sort based on class attribute: \` sorted(student~objects~,
    key=attrgetter(\'grade\', \'age\')) \`
-   Note: itemgetter for list/tuple and attrgetter is for class

# Comparison Functions [How does the functools cmp\_ to\_ key function works in Python? - GeeksforGeeks](https://www.geeksforgeeks.org/how-does-the-functools-cmp_to_key-function-works-in-python/)

# functools.cmp\_ to\_ key(callable) {#functools.cmp_-to_-keycallable collapsed="true"}

## A comparison/callable function is any callable that accepts two arguments, compares them, and returns a negative number for less-than, zero for equality,

## example:

## python

``` python
import functools
def mycmp(student1, student2):
    print("comparing ", student1, " and ", student2)
    if student1.age > student2.age:
        return 1
    elif student1.name < student2.name:
        return -1
    else:
        return 0
print(sorted([student("James", 12), student("Mike", 11)], key=functools.cmp_to_key(mycmp)))

```

# Iterator {#iterator heading="3" term="An iterator is a Python object that implements a specific interface. ~iter___~ return instance of iterator and __next()__ method steps the iterator on cycle and return a value to next object" id="65137d16-a06a-40e4-b28e-5fa4474017d5"}

# **functools: cache** {#functools-cache collapsed="true"}

## \@functools.\*cache\*(*user\_ function*)

## python

``` python
import functools
@functools.cache
def factorial(n):
    return n * factorial(n-1) if n else 1
factorial(10)      # no previously cached result, makes 11 recursive calls

```

# **list comprehension** {#list-comprehension collapsed="true"}

## [When to Use a List Comprehension in Python -- Real Python](https://realpython.com/list-comprehension-python/)

## baisic

### python

``` python
List = [character for character in [1, 2, 3]]
print(List) #[1, 2, 3]
[i for i in range(11) if i % 2 == 0] #[0, 2, 4, 6, 8, 10]
matrix = [[j for j in range(3)] for i in range(3)] # 3x3 matrix

lis = [num for num in range(100)
       if num % 8 == 0 if num % 10 == 0] # [0, 40, 80]

string = 'Geeks4Geeks'
# Toggle case of each character
List = list(map(lambda i: chr(ord(i) ^ 32), string))
# ['g', 'E', 'E', 'K', 'S', '\x14', 'g', 'E', 'E', 'K', 'S']

# Reverse each string in tuple
List = [string[::-1] for string in ('Geeks', 'for', 'Geeks')]
# ['skeeG', 'rof', 'skeeG']

# Remove Multiple Values
ls = ['One', 'Two', 'Three', 'Three']
to_remove = ['Three', 'Four']
ls = [x for x in list(ls) if x not in to_remove]
#Tree BFS
[child for child in (n.left, n.right) if child]

```

# Map, Filter, Reduce and Zip {#map-filter-reduce-and-zip id="6506c411-3211-4b0c-9647-637d211344b3" collapsed="true"}

## [Map, Filter, Reduce - Learn Python - Free Interactive Python Tutorial](https://www.learnpython.org/en/Map%2C_Filter%2C_Reduce)

### Map and Filter return iterator (not list)

\<a id=\"map\"\>Map\</a\>

### \*Map(func, **iterables)**

1.  Samples

    ``` python
    list(map(str.upper,  ['alfred', 'tabitha', 'william', 'arla']))
    list(map(round,  [3.56773, 5.57668, 4.00914, 56.24241, 9.01344, 32.00013], range(1, 7)))
    # 3rd parameter is parameter to round
    list(map(lambda x, y: (x, y), ['a', 'b', 'c', 'd', 'e'], [1, 2, 3, 4, 5]))
    list(map(lambda x, y, z: (x+y)*z, [1, 2, 3, 4, 5], [10, 20, 30, 40, 50], [1, 2, 3, 4, 5]))
    #[11, 44, 99, 176, 275]
    ```

### **Filter(func, iterable)**

1.  list(filter(lambda v: v \> 75, \[66, 90, 68, 59, 76, 60, 88, 74, 81,
    65\]))

2.  filter and list comprehension

    ``` python
    [<exp1> for <var> in <iterable> if <logic expression>]
    [x for x in l if x%2]

    ```

### **reduce(func, iterable\[, initial\])** {#reducefunc-iterable-initial collapsed="true"}

1.  python

    ``` python
    from functools import reduce
    numbers = [3, 4, 6, 9, 34, 12]
    def custom_sum(first, second):
        return first + second
    result = reduce(custom_sum, numbers)
    print(result)

    ```

2.  Another using reduce to implement #Trie [*DSA/Trie*]{.spurious-link
    target="DSA/Trie"}

    1.  python

        ``` python
        Trie = lambda: defaultdict(Trie) #constructor return default dict
        trie = Trie() # dict to lambda
        END = True

        # Insert words into the trie
        words = ["apple", "banana", "apricot", "bear", "beach"]
        for word in words:
            reduce(dict.__getitem__, word, trie)[END] = word

        ```

    2.  e.g. word = \'apple\'. then trie\[\'a\'\] = dict{\'p\':
        dict{\'p\': dict{\'l\': dict{\'e\': dict{True:\'apple\'}}}}}

### Zip

1.  creates an iterator that will aggregate elements from **zero to
    more** iterables.

    1.  zip(\[1, 2\]); zip(\[1, 2\], \[\'a\', \'b\'\])

    2.  zip most useful to create []{#dict}

    3.  List comprehensions

        `[x * y for x, y in zip([1, 2, 3], [3, 4, 5])]` **\*\***

# Heap #heapq {#heap-heapq collapsed="true"}

## Operations:

### peek: there are **no peek**, use heap\[0\] instead

### heappush

### heappop

1.  python

    ``` python
    h = []
    for value in [1, 3, 5, 7, 9, 2, 4, 6, 8, 0]:
        heappush(h, value)
    return [heappop(h) for i in range(len(h))]

    ```

### heappushpop(heap, item) push item and pop and return top element

### heapify(x) : transform list x to heap, inplace O(n)

### heapreplace(heap, item) pop smallest item and push new item, raise error if empty. It is efficient for fixed size heap. It works like poppush

### merge: merge multiple sorted input into a single sorted. It return a iterable(not al ist)

### **nlargest** & **nsmallest**: return list of n largest/smallest elements, Equivalent to: `sorted(iterable, key=key, reverse=True/False)[:n]`

# Counter {#counter collapsed="true"}

## [Python\'s Counter: The Pythonic Way to Count Objects -- Real Python](https://realpython.com/python-counter/)

## counter.update(): the implementation provided by \*Counter\* adds existing counts together. It also creates new key-count pairs when necessary.

### python {#python-7}

``` python
>>> from collections import Counter
>>> letters = Counter({"i": 4, "s": 4, "p": 2, "m": 1})
>>> letters.update("missouri")
>>> letters
Counter({'i': 6, 's': 6, 'p': 2, 'm': 2, 'o': 1, 'u': 1, 'r': 1})
>>> sales = Counter(apple=25, orange=15, banana=12)
>>> # Use a counter
>>> monday_sales = Counter(apple=10, orange=8, banana=3)
>>> sales.update(monday_sales)
>>> sales
Counter({'apple': 35, 'orange': 23, 'banana': 15})

```

### keys(): list of all keys

### values(): list of all values

1.  python

    ``` python
    cnt = Counter("AABC")
    total = sum(cnt.values())   # 4

    ```

### most\_ common() This method returns a list of (object, count) sorted by the objects' current count

**\***

# Enum {#enum collapsed="true"}

## python {#python-9}

``` python
from enum import Enum

# class syntax
class Color(Enum):
    RED = 1
    GREEN = 2
    BLUE = 3

# functional syntax  👍
Color = Enum('Color', ['RED', 'GREEN', 'BLUE'])
my_color = Color.RED

```

# Const/Final {#constfinal collapsed="true"}

## python {#python-10}

``` python
from typing import Final

PI: Final =  3.14

```

# [*Comments*]{.spurious-link target="Comments"} {#comments collapsed="true"}

## [*Sep 21st, 2023*]{.spurious-link target="Sep 21st, 2023"} {#sep-21st-2023 collapsed="true"}

### ((650c181a-1ea2-475c-a09b-35a4aa6ecd39))

**\*\***
