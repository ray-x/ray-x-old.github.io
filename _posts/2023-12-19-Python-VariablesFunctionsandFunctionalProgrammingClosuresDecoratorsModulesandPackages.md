---
course-repo: "https://github.com/fbaptiste/python-deepdive"
institute: udemy
instructor: "Dr. Fred Baptiste https://www.udemy.com/user/fredbaptiste/"
language: python
start-date: \[\[Sep 16th, 2023\]\]
tags: Python, deep-dive
type: programming
---

# [Python+Deep+Dive+1.pdf](../assets/Python+Deep+Dive+1_1694868717879_0.pdf) {#pythondeepdive1.pdf heading="3"}

# Refresher {#refresher heading="2" collapsed="true"}

## Multi-line Statement in Python: {#multi-line-statement-in-python heading="3" collapsed="true"}

### To extend the statement to one or more lines we can use braces {}, parentheses (), square \[\], semi-colon ";", and continuation character slash "\\".

### For string you can use `'''` or `"""` for a multiple line string

``` python
list = [5,
        4, 3, 2, 1
        ]
print('Initializing a list using the\
 Implicit multi-line statement', list)
g = """geeks
for
geeks""" 
# Initializing a mathematical expression
# using the Implicit multi-line statement.
add = (50 +
       40 -
       52)
if a \
  and b:
  pass
```

## Variable Naming {#variable-naming heading="3" collapsed="true"}

### ((6505ac52-5d0c-4272-8c97-ea3ab05e7dcd))

## Condition Expression {#condition-expression heading="3" collapsed="true"}

### `5 < a < 7` vs `5<a and a<7`

### ternary

1.  `b = 1 if a < 5 else 2`

2.  `var = exp1 if con-exp2 else exp2`

## Continue, break, while, else, try, catch, finally {#continue-break-while-else-try-catch-finally heading="3" desc="it is important to figure out when statements will be executed"}

### The `continue` statement skips the current iteration of a loop and continues with the next iteration.

### `finally` will be executed even with `continue|break`

### loop altogether, and the program continues after the loop. aka `goto loop_exit`

### Inside try-except-finally

``` python
# in a for Statement
for x in range(2):
  try:
      print('trying...')
      continue   #break 
      print('still trying...')
  except:
      print('Something went wrong.')
  finally:
      print('Done!')
print('Loop ended.')
# Prints trying...
# Prints Done!
# Prints trying...
# Prints Done!
# Prints Loop ended.
```

### finally clause is executed before starting(break; exit) the next iteration.

### `break` with `for/while-else`

1.  If the loop terminates \*prematurely\* with `break`, the else clause
    won't be executed.

    ``` python
    # Break the for loop at 'blue'
    colors = ['red', 'green', 'blue', 'yellow']
    for x in colors:
        if x == 'blue':
            break
        print(x)
    else:
        print('Done!') #will never executed
    # Prints red green
    ```

# Variable {#variable heading="2" collapsed="true"}

## *Everything* is object {#everything-is-object heading="3"}

### e.g. int is \<Class \'int\'\>

## Python Garbage Collection {#python-garbage-collection heading="3"}

### Viewing reference counts in Python

``` python
>>> import sys
>>> a = 'my-string'
>>> sys.getrefcount(a)
>>> del a  # set ref count to 0
>>> import gc
>>> gc.get_count()
(595, 2, 1)
>>> gc.collect()
577
>>> gc.get_count()
(18, 0, 0)
```

### Disabling the garbage collector

1.  [Dismissing Python Garbage Collection at Instagram \| by Instagram
    Engineering \| Instagram
    Engineering](https://instagram-engineering.com/dismissing-python-garbage-collection-at-instagram-4dca40b29172)

2.  When share memory or object reused repeatedly disable GC can save

### Python object id() is used to get location of a object

## Type {#type heading="3"}

### Python is Dynamic typed, use `type()` to get object type

### Python access variable data value through reference. Object can bind to different type (change reference) durning execution

## Mutable vs immutable {#mutable-vs-immutable heading="3"}

### ((650790fd-e50a-4807-9705-97324dbb967b))

### Inmutable: create a new object if value changed, `id(my_var)` changes when value changed.

### Why it is important?

1.  Side-effect

2.  performance

### Notes

1.  mutable can change id. E.g. `list.appen(val)` vs `list += [val]` vs
    `list = list+[val]`. The last `list=list+[val]` creates a new object

2.  use `append` or `+=` when possible

3.  A immutable object can have mutable objects

    ``` python
    t = ([1], [3])
    t[0].append(2)
    ```

4.  immutable are safe from unintended side-effect (e.g. func call)

5.  to prevent side-effect, use copy() to shallow copy a mutable
    object(e.g. list)

## Share reference {#share-reference heading="3"}

### python share reference by default

((65079bf5-d1fd-48ef-aa24-680ec28b97cd))

### With mutable objects e.g. list, Python will **NEVER** create shared reference. This may confusing with

``` python
a=[1, 2]
b=a #reference
c=[1, 2]  #does not share with a/[1,2] 
```

### Python pr-create values \[-5, 256\] so if value in that range, it will share reference

## Equality {#equality heading="3"}

### `is` identity operator `id(a) == id(b)`

### Sample

``` python
a = 10
b = a
a is b
a == b
a = [1]
b = [1]
a is not b
```

### All objects of None are same. Same id and same value `a is None`

## Numbers {#numbers heading="3" collapsed="true"}

### Python does handle allication memory/bytes for numbers based on the value, e.g. $2^{1000}$ use 160 bytes

### The larger the number the more memory

### `floor` is largest(in stardard number order) {#floor-is-largestin-stardard-number-order collapsed="true"}

``` python
floor(3.3) -> 3
floor(-3.3) -> -4
```

1.  `/` divide -\> float

2.  `//` divide floor -\> int

3.  `%` reminder -\> int

4.  int(10.9) -\> truncation 10

### Integer / int {#integer-int collapsed="true"}

1.  constructor `int(10.1); int(True); int(Decimal("10.2")); int("10")`

2.  With Base. `int("1010", 2) ; int("1010", base=2)`

3.  `bin() -> "0b1010";  oct() -> "0o12"; hex() -> "0xa"`

4.  `sign(x)`: `1 if x >= 0 else -1`

### Rational and Fraction

1.  Franction

    1.  #+BEGIN~SRC~ python

        From factions import Fraction Fraction(3,4) #3/4 numerartor,
        denominator Fraction(3.4) Fraction(\'3.4\') Fraction(\'3.4\') \*
        Fraction(3.4) Fraction(math.sqrt(2)) \# will be comn In \[17\]:
        y=Fraction(sqrt(2)) In \[18\]: y Out\[18\]:
        Fraction(6369051672525773, 4503599627370496)
        y.limit~denominator~(10)

        ```{=org}
        #+END_SRC
        ```

    2.  use y.limit~denominator~(10) to round denominator to close to 10

### Float {#float collapsed="true"}

1.  IEEE 754 double-precision binary float aka binary 64

    1.  sing 1bit

    2.  exponent 11bit

    3.  significant 52 bit

2.  Equality

    1.  `math.isclose(a, b, *, rel​​​​​_​​​​​​​tol=1e - 9, abs​​_​​tol=0.0)`

        1.  e.g. `math.isclose(3.3, 1+2.3000)`

    2.  `round(val, digits)` e.g. `round(3.1415, 2)  -> 3.14`

    3.  You should always use isclose for compare float

3.  Float to int

    1.  `truncation|math.trunc()`, `floor`, `ceiling`, `rounding`

    2.  trunc keep the int part. same as `int(val)`

    3.  `floor` largest integer LE to the val

    4.  `ceiling` min{i \>= x}

    5.  round(val, n). closest multiple of 10^-n^ , n default to 0 so
        round(val) -\> int(val)

        1.  round(1.25, 1) -\> 1.2 (to nearest val with even least
            significant digit)

        2.  Banker\'s Rounding

### decimal {#decimal collapsed="true"}

1.  Unlike [floats](https://www.pythontutorial.net/advanced-python/python-float/),
    Python represents decimal numbers exactly. And the exactness carries
    over into arithmetic

2.  Decimal always associates with
    a [context](https://www.pythontutorial.net/advanced-python/python-context-managers/) that
    controls the following aspects:

    1.  Precision during an arithmetic operation (default 28)

    2.  Rounding algorithm

3.  Sample

    ``` python
    import decimal
    from decimal import Decimal
    decimal.getcontext().prec = 2
    pi = Decimal('3.14159')
    print( pi * radius * radius )
    pi = Decimal(sign, (d1, d2, d3, ...), exp) 
    pi = Decimal (0, (3, 1, 3, 1, 5), 4)

    10.0 == Decimal('10.0')  # .0 will be use
    0.1 != Decimal('0.1') #  print('{:.20f}'.format(0.1)) 0.10000000000000000555
    ```

4.  Decimal arithmetic operators

    1.  `//` and `%`

    2.  `Decimal(a)//Decimal(b)` -\> `trunc(a/b)`

### Complex number {#complex-number collapsed="true"}

1.  use `cmath`

## Boolean {#boolean heading="3"}

### Boolean is subclass of `int` but it is used in totally different way. Every object in python has a `truth value` (truthiness)

### `bool` class {#bool-class collapsed="true"}

1.  `True` and `False`

2.  isubclass of int `issubclass(bool, int)`

3.  wired truth of bool

4.  `isinstance(True, int)` -\> `True`

5.  True -\> 1; False-\>0 (int(True)-\>1; True == 1 ; True \> False)

    1.  True + True = 2

6.  They are singleton object

7.  You can use both `a==True` and `a is True` because it is singleton

### Truthy {#truthy collapsed="true"}

1.  All objects are True except

    1.  None

    2.  False

    3.  classes implement `__bool__` or `__len__` that return `False` or
        `0`.

        Default of `__bool__` is `return self != 0` e.g. `bool(100)`
        will execute `int(100).__bool__()` and therefore return result
        of `100 != 0`

    4.  Based on above following is `False`:

        1.  0 **in any numeric type** (0, 0.0, 0+0j)

        2.  empty collections (list, tuple, string, dict set)

2.  for [*javascript*]{.spurious-link target="javascript"}
    ((650504dd-d2ad-48f6-b26b-b98d6c5e99dd))

    **\*\***

### Logical operation precedence

1.  ()

2.  compare `>, < == !=`

3.  `in` `is`

4.  `and`

5.  `or`

### Short-Circuit

1.  Be care that when short-circuited, part of the expression may not
    executed

### Logic operations

1.  X or Y is equal to `X if X else Y`

    ``` python
    x = 32
    y = 7
    print(x or y)  # 32
    x = 0
    y = 'abc'
    print(x or y) # abc
    ```

2.  `X and Y` `X if not X else Y`

    1.  #+BEGIN~SRC~ pyhon

        x = 10 y = x and 20/x \# y = 2

        z = (s and s\[0\]) or \'\' \# if s: return s\[0\]; else return
        \'\'

        ```{=org}
        #+END_SRC
        ```

### Comparison operators

1.  chained comparisons

    1.  In Python, chaining comparison operators is a way to simplify
        multiple comparison operations by stringing them together using
        logical operators. This is also known as "chained comparisons"
        or "chained comparison operators".

    2.  `a==b==c`

    3.  `a<b<c`

    4.  `a<b>c`

    5.  `a>b<c`

    6.  `a<b<c<d`

    7.  #+BEGIN~SRC~ python

        exp1 = a \<= b \< c \> d is not e is f

        ```{=org}
        #+END_SRC
        ```

# Function {#function heading="2" collapsed="true"}

## Argument and parameter {#argument-and-parameter heading="2"}

### Positional and keyword arguments

1.  It following C++ rule. If a positional parameter is defined with
    default value, every positional parameter after it **must** given a
    default value

    ``` python
    def myfun(a, b=100, c=0): # a positional
      pass
    myfun(1)
    myfun(1, 2)
    myfun(1, 2, 3)
    ```

### keyword argument

1.  #+BEGIN~SRC~ python

    myfun(a=1, b=2, c=3) my(1, 2, c=3) myfun(1, c=2) #b skipped and will
    use default value of 100 myfun(c=3, a=1, b=2) \# it is ok not follow
    same order myfun(a=1, 2, 3) \# ❌not correct, the rest after \`a=1\`
    must be named

    ```{=org}
    #+END_SRC
    ```

### Function arguments list is ((650994bb-61c3-4e01-b5a0-e7eeda531610))

1.  `*arg` to accept variable length arguments

    1.  example

        ``` python
        def func(a, b, c)
          pass
        l = [1, 2, 3]
        func(*l)  #unpack  l from list to numbers

        def func2(a, b, *args)
          print(a, b, args)
        func2(10, 20, 1, 2, 3)  # 10, 20 (1, 2, 3)

        def avg((args):
          return args and xxxxsum(args)/len(args)
        ```

    2.  all arguments after `*arg` must be \^^keyword^\^\^ arugments

        ``` python
        def func2(a, b, *args, d)
          print(a, b, args)
        func(1, 2, 3, 4, d=5)
        ```

    3.  \^^\*^\^\^ without name `def func(*, d)` means there are no more
        positional args, you must provides keyword arguments

        1.  it means you can not pass arguments other than \<\<keyword
            argument\>\>

        2.  e.g `func(d=32)`

    4.  \^\^/\^\^ : `def mod(x, y, /)` means x, and y are \<\< position
        ONLY parameters \>\>

2.  `**kwargs` to unpack dict

    1.  used to group keywords arguments

    2.  can be spicified even if positional arguments not been exausted

    3.  **NO** parameters can come after \*\*kwargs

    4.  Sample

        ``` python
        def func(*, d, **kwargs):
          print(d, kwargs)
        func(d=1, a=2, b=3)   # d=1, kwargs = {'a': 2, 'b':3}
        def func2(*args, **args):
          print(args, kwargs)
        func(1, 2, a=10, b=20)  # (1, 2) {a:10, b:20}
        ```

    5.  you **can not** do this: func(a, b, \*, \*\*kwargs)

3.  Default arguments #pitfall

    1.  It created once, the value should be treat as const. If you need
        the argument to be variable, e.g. `datetime.now()` do not use
        default argument.

        1.  Solution: \^^default^ to None\^\^

    2.  Another case, if initialize a default parameter with collection
        (e.g. list, dict). As same reason above, it will freeze a
        collection object to variable, if the function reused, the
        collection object will be resused and it may have incorrect
        values

        1.  Solution: \^^default^ to Nono, not empty collection\^\^

        2.  sample:

            ``` python
            def func(l =[]):
              l.appen(1)
              return l

            print(func())
            print(func())  # 1, 1
            ```

        3.  This can also be used for recursion remember the results
            #memoization

            1.  factorial example:

                ``` python
                def factorial(n, cache={}):
                  if n<1:
                    return 1
                  elif n in cache:
                    return cache[n]
                  else:
                    k = factorial(n-1)*n
                    cache[n]=n*factorial(n-1)
                    return k
                ```

## First-Class Functions {#first-class-functions heading="2"}

### High order functions {#high-order-functions heading="3"}

1.  A function take parameter of another function as arguments

### Docstring PEP 257 {#docstring-pep-257 heading="3" collapsed="true"}

1.  🧑‍🏫A **docstring** is a string literal that occurs as the \^^first^
    statement\^\^ (exclude comments) in a module, function, class, or
    method definition. Such a docstring becomes the \_~doc~\_\_ special
    attribute of that object.

2.  function docstr stored in function. \_ ~doc~ \_ \_

3.  Sample:

    ``` python
    def root():
        """Return the pathname of the KOS root directory."""
        global _kos_root
        if _kos_root: return _kos_root
          ...
    def function(a, b):
        """function(a, b) -> list"""

    def complex(real=0.0, imag=0.0):
        """Form a complex number.
        Keyword arguments:
        real -- the real part (default 0.0)
        imag -- the imaginary part (default 0.0)
        """
    ```

### Annotations PEP 3107 {#annotations-pep-3107 heading="3" collapsed="true"}

1.  🧑‍🏫Function annotations are \^^arbitrary^ python expressions\^\^ that
    are associated with various part of functions.

2.  Benefit: help string(e.g. with sphinx), compile check

3.  it stored in \~ \_~annotations~\_\_\~ in K:V format

4.  \<\<type hints\>\>

    1.  type hints is one form of annotations

5.  Sample:

    ``` python
    def f(a:str = 'a', b: [1,2,3]) ->str:
      ...
    def f2(a:str) -> 'a repeated ' + str(max(x,y)) + ' times'
      ...
    ```

### Lambda Expressions {#lambda-expressions alias="anonymous function" heading="3" collapsed="true"}

1.  Limitations

    1.  single line expression

    2.  no assignment

    3.  no annotations

2.  Syntax

    ``` python
    lambda arguments : expression

    lambda s: s[::-1].upper()
    def appply_func(x, fn):
      return fn(x)
    apply_func(2, lambda x: x**)
    ```

3.  Usages

    1.  use in sorted `key`

        ``` python
        sorted(d, key = lambda s : s.upper())
        # randomisze a string
        sorted(d, key = lambda x: random.random())
        ```

### Introspection {#introspection heading="3"}

1.  `__name__` function name

2.  `__defaults__`, `__kwdefaults__` defaults values

3.  `__code__` the code objects includes

    1.  `co_varnames` : parameters

    2.  `co_argcount`

4.  []{#inspect}module

    1.  isroutine: func or method

    2.  getsource \| getmoudle \| getcomments \| signature

### callable {#callable heading="3" descr="" tags="[[functional programming]]"}

1.  {{cloze a object like (but not **limited to**) []{#functions}and
    []{#methods}}}

2.  `callable()` check if a object is callable

3.  []{#Class}is callable

4.  generators, coroutines, asynchronous generators

5.  any objects implements `__call__` []{#Class}

### {{embed ((6506c411-3211-4b0c-9647-637d211344b3))}} {#embed-6506c411-3211-4b0c-9647-637d211344b3 heading="3"}

### Partial function {#partial-function desc="A function that is created by fixing a certain number of arguments of another function" tags="[[functional programming]]" heading="3"}

1.  samples:

    1.  #+BEGIN~SRC~ python

        from functools import partial

        def f(a, b, c, x): return 1000\*a + 100\*b + 10\*c + x

        g = partial(f, 3, 1, 4)

        print(g(5))

        add~part~ = partial(add, c = 2, b = 1)

        print(add~part~(3))

        ```{=org}
        #+END_SRC
        ```

2.  Use

    1.  Callback signature

    2.  Integration with other API

### Operator {#operator heading="3"}

1.   [[PROPERTIES]{.smallcaps}]{.tag tag-name="PROPERTIES"}

    :desc:
    The [operator](https://docs.python.org/3/library/operator.html#module-operator) module
    exports a set of efficient functions corresponding to the intrinsic
    operators of Python. :url:
    <https://docs.python.org/3/library/operator.html#module-operator>
    :tags: [*functional programming*]{.spurious-link
    target="functional programming"}

    ::: {.END .drawer}
    :::

    1.  iadd iand iconcat ifloordiv ilshift imod imul imatual ior ipow
        isub ixor itruediv

2.  attrgetter(attr)

    1.  返回一个可从操作数中获取 *attr* 的可调用对象。
        如果请求了一个以上的属性，则返回一个属性元组。
        属性名称还可包含点号。 例如：

        1.  在 f = attrgetter(\'name\') 之后，调用 f(b) 将返回 b.name。

        2.  在 f = attrgetter(\'name\', \'date\') 之后，调用 f(b) 将返回 (b.name, b.date)。

        3.  在 f = attrgetter(\'name.first\', \'name.last\') 之后，调用 f(b) 将返回 (b.name.first, b.name.last)

3.  `__getattr__`

    1.  If attr not existed in object this function will be called. e.g.
        `obj.func_ont_exist` or `getattr(obj, 'not_existed')`

4.  `__getattribute__`

    1.  always triggered when reference a attribute inside a object

5.  itemgetter(item\|\*item)

    1.  返回一个使用操作数的 [`__getitem__()`](https://docs.python.org/zh-cn/3/library/operator.html#operator.__getitem__) 方法从操作数中获取 /item/ 的可调用对象。
        如果指定了多个条目，则返回一个查找值的元组。

    2.  sample

        ``` python
        itemgetter(1)('ABCDEFG') #B
        itemgetter(1, 3)('ABCDEFG')  #('B', 'C')
        ```

6.  methodcaller(*name*, /, \*args, \*\*kwargs)

    1.  返回一个在操作数上调用 /name/ 方法的可调用对象。
        如果给出额外的参数和/或关键字参数，它们也将被传给该方法

        ``` python
        def methodcaller(name, /, *args, **kwargs):
            def caller(obj):
                return getattr(obj, name)(*args, **kwargs)
            return caller
        class MyClass:
          def test(self, arg):
            print("test", arg)
        obj = MyClass()
        testfun = attrgetter('test')(obj)
        testfun("aaa")
        methodcaller('test', 'aaa')(obj)
        ```

# Closure {#closure heading="2" tags="fp, closure" desc="function object that remembers values in enclosing scopes even if they are not present in memory" collapsed="true"}

## Abstract {#abstract heading="3"}

## Questions, keywords and cues {#questions-keywords-and-cues heading="3"}

### :Questions-keywords-cues:

-   What do I already know?
-   Strengths and weaknesses?
-   When to apply this theory?
-   How valid are the research methods?
-   How strong is the evidence?
-   How logical is the argument?
-   How does this fit in to other research in the field?
-   What do I need to find out next?

::: {.END .drawer}
:::

### :main-idea-checkbox:

-   What is this aims?
-   What is the their research question?
-   What is the author arguing?
-   What is their answer to the question?
-   What points support their argument?
-   What are their main reasons?
-   What evidence have they used to support their argument?
-   What's the significance of these facts?
-   What principle are they based on?
-   How can I apply them?  How do they fit in with what I already know?
-   What's beyond them?
-   What\'re supporting details and explanations?

::: {.END .drawer}
:::

### Scopes and namespace {#scopes-and-namespace tags="LEGB" desc="*Local -> Enclosing -> Global -> Built-in*" heading="4"}

1.  [python variable
    scopes](https://favtutor.com/resources/images/uploads/mceu_14589579711675226532035.jpg)

2.  It is important when a symbol is hide/blocked by another symbol

### built-in scope {#built-in-scope heading="4" collapsed="true"}

1.  `print`, `True`, `False` etc are located in bult-in scope. If a
    symbol is not in *module* scope or current LEG, search in built-in
    scope. This is #LEGB

### Local Scope {#local-scope heading="4" collapsed="true"}

1.  inside a function. So it also called *function local scope*

### Enclosing Scope {#enclosing-scope collapsed="true"}

1.  **nonlocal scope**

2.  **nonlocal**

    1.  The `nonlocal` keyword is used in nested functions to declare
        that a variable refers to a variable in the nearest enclosing
        scope that is not global. This means if you have a nested
        function and you want to modify a variable from the outer
        (enclosing) function, you\'d use `nonlocal`. Sometime the
        *nonlocal* variable also been called **free variable**

    2.  free variable

    3.  Use the keyword `nonlocal` to declare that the variable is not
        local.

    4.  When nonlocal can be omitted

        1.  if it is read after write or read only, you can skip
            `nonlocal` keyword

3.  nested function create an outer and inner scope, use **nonlocal**
    keyword to refer to the outer scope instead of create a new local
    variable

    ``` python
    def outer():
        string = "Favtutor" # Local Variable
        def inner():
            nonlocal string #declaring a non local variable
            string= "Python Favtutor Classes" # Overwriting value of a variable string
            print("inner function:", string)
        inner()
        print("outer function:", string)

    outer()
    ```

### Global scope {#global-scope collapsed="true"}

1.  A variable created in the main body of the Python code is a
    **global** variable and belongs to the global scope. aka *module
    scope* or *file scope*. It spans a **single file** only

2.  Global Keyword

    1.  If you need to create a global variable, but are stuck in the
        local scope, you can use the `global` keyword.

    2.  The `global` keyword makes the variable global.

        ``` python
        def myfunc():
          global x  # create a global variable
          x = 300
        myfunc()
        print(x)
        ```

### Global and local {#global-and-local collapsed="true"}

1.  **The main difference is that Global is used to access and modify
    global variables from within a function, while nonlocal is used to
    access and modify variables from the nearest enclosing scope that is
    not global.**

2.  when python encounter a func definition at compile time. It scans
    for labels/var that have assigned to them **anywhere** in the
    function. If the label has not been specified as *global* it is a
    local

3.  Var referenced but not assigned anywhere in the func will not be
    local and python at runtime look for them in **enclosing** scopes

4.  Nonlocal declarations in a local scope do not require the variable
    to be pre-bound (it declared in outer scope), which is another
    fundamental distinction between them. These variables must already
    have been bound in the surrounding namespace(outer function) to
    avoid syntax errors.

5.  While a nonlocal statement allows for the alteration of an enclosing
    scope variable in the local scope, a global statement allows for the
    modification of a global variable in the local scope. Nonlocal
    variables must already exist, although global variables can be
    declared with brand-new variables.

6.  Sample

    ``` python
    a = 10
    def f3():
      global a
      a = 100 # this refer to the a at line 1
    def f4():
      print(a)  # this refer to a at next line and will throw a runtime error
      a = 100
    ```

### **del** a symbol in current scope {#del-a-symbol-in-current-scope heading="4" collapsed="true"}

1.  e.g

    ``` python
    print = lambda n: print(2**n)
    print(3)
    del print
    ```

### Cell object {#cell-object heading="4" id="650f9d5c-c95d-41d3-8f60-6d6ada6c32f2" collapsed="true"}

1.  **Cell** objects are used to implement variables referenced by
    multiple scopes. For each such variable, a cell object is created to
    store the value; the local variables of each stack frame that
    references the value contains a reference to the cells from outer
    scopes which also use that variable. When the value is accessed, the
    value contained in the cell is used instead of the cell object
    itself. This de-referencing of the cell object requires support from
    the generated byte-code; these are not automatically de-referenced
    when accessed. Cell objects are not likely to be useful elsewhere.

2.  ((650f9ddb-a02a-45cf-9524-8c395f42f66e))

3.  Cell is important to understand **free variables** used in closure

## 📖 Closure {#closure-1 heading="3" desc="A function object that has access to variables in its lexical scope, even when the function is called outside that scope. In simpler terms, the inner function remembers the environment in which it was created."}

### When closure created, it put the **nonlocal** and **global** variable into a dict ((650f9d5c-c95d-41d3-8f60-6d6ada6c32f2)) and closure can be introspect with `__closure__`

### if there is no ((65100808-8929-4581-a57b-c1f9470e4eb6)) there is no closure

### Use closure to remember state {#use-closure-to-remember-state heading="4" collapsed="true"}

1.  ((650fb53c-bad9-4c9b-87c7-acc3a3d2a8b8))

2.  When counter() created a closure. It include a reference to
    counter/cell. So each time `fn()` called, count will change

### Multiple instance of Closures {#multiple-instance-of-closures heading="4" collapsed="true"}

1.  Each time create a new closure, a **new** scope/env/capture will
    also created.

    ``` python
    f1 = counter()
    f2 = counter()
    f1() # -> 1
    f1() # -> 2
    f2() # -> 1
    ```

### Shared scope and share reference/cell {#shared-scope-and-share-referencecell heading="4" collapsed="true"}

1.  Following code

    ``` python
    adders = []
    for n in range(1, 4):
      adders.append(lambda x: x + n)
    adders[0](1)  -> 4
    adders[1](1)  -> 4
    adders[2](1)  -> 4

    # vs
    adders = []
    for n in range(1, 4):
      adders.append(lambda x, y=n: x + y)
    adders[0](1)  -> 2
    adders[1](1)  -> 3
    adders[2](1)  -> 4

    ```

2.  The reason n is **3** for each adder closure is:

    1.  n is a share scope object in for loop

    2.  it does not recreated each time

    3.  each adder has a ((650f9d5c-c95d-41d3-8f60-6d6ada6c32f2)) which
        is reference to `n`

    4.  It is important to know closure scope value is stored in
        ((650f9d5c-c95d-41d3-8f60-6d6ada6c32f2)) and store reference,
        when the value reference pointing to changed, closure value will
        also change .

    5.  Python does not evaluate free vars n until adders\[i\] func is
        called. And all of then refer to same n(3) when it is called

### Replace Class with closure {#replace-class-with-closure collapsed="true"}

1.  In many cases, the only reason we might have a single-method class
    is to store additional state for the use in method.

2.  A request class

    ``` python
    import requests
    class SourceTemplate:
        def __init__(self, url):
            self.url = url
        def load(self, **kwargs):
            return requests.get(self.url.format_map(kwargs))
    github = SourceTemplate('https://api.github.com/repositories?since={since}')
    github.load(since=200).json()
    ```

3.  A closure implementation

    ``` python
    def sourcetemplete(url):
        def load(**kwargs):
            return requests.get(url.format_map(kwargs))
        return load
    load = sourcetemplete('https://api.github.com/repositories?since={since}')
    load(since=200).json()
    ```

## Recites {#recites heading="3"}

### :HOWTO-RECITE:

Cover the notetaking column with a sheet of paper.  Then, looking at the
questions or cue-words in the question and cue column only, say aloud,
in your own words, the answers to the questions, facts, or ideas
indicated by the cue-words.

::: {.END .drawer}
:::

### main points

\*\*

# Decorator {#decorator heading="2" tags="fp, decorator" desc="decorator is a design pattern that allows you to modify the functionality of a function by wrapping it in another function." collapsed="true"}

## Abstract {#abstract-1 heading="3"}

### The outer function is called the decorator, which takes the original function as an argument and returns a modified version of it.

### So, in the most basic sense, a decorator is a callable that returns a callable.

### ((65101822-3477-4dbd-bf27-c6d41cb38579))

## Questions, keywords and cues {#questions-keywords-and-cues-1 heading="3" collapsed="true"}

### :Questions-keywords-cues:

-   What do I already know?
-   Strengths and weaknesses?
-   When to apply this theory?
-   How valid are the research methods?
-   How strong is the evidence?
-   How logical is the argument?
-   How does this fit in to other research in the field?
-   What do I need to find out next?

::: {.END .drawer}
:::

### :main-idea-checkbox:

-   What is this aims?
-   What is the their research question?
-   What is the author arguing?
-   What is their answer to the question?
-   What points support their argument?
-   What are their main reasons?
-   What evidence have they used to support their argument?
-   What's the significance of these facts?
-   What principle are they based on?
-   How can I apply them?  How do they fit in with what I already know?
-   What's beyond them?
-   What\'re supporting details and explanations?

::: {.END .drawer}
:::

### Using nested functions

``` python
def counter(fn):
    count = 0
    def inner(*args, **kwargs):
        nonlocal count
        count += 1
        print('Function {0} was called {1} times'.format(fn.__name__, count))
        return fn(*args, **kwargs)
    return inner

def add(a, b=0):
  "return sun of two integers"
  return a + b
add = counter(add)
add(1, 2) # Function add was called 1 times 3
```

### Pythonic way

``` python
@counter
def mult(a: float, b: float=1, c: float=1) -> float:
  "mult return products of three number"
  return a * b * c
```

### There is a minor problems that mult is no longer mult after wrapped by operator. The `__doc__` and `__name__` changed. That when `@wraps is needed`

``` python
def counter(fn):
    count = 0
    @wraps(fn)
    def inner(*args, **kwargs):
        nonlocal count
        count += 1
        print("{0} was called {1} times".format(fn.__name__, count))
    return inner
```

It is same as this:

``` python
def counter(fn):
    count = 0

    def inner(*args, **kwargs):
        nonlocal count
        count += 1
        print("{0} was called {1} times".format(fn.__name__, count))
    inner.__name__ = fn.__name__
    inner.__doc__ = fn.__doc__
    return inner
```

And also this:

``` python
def counter(fn):
    count = 0

    def inner(*args, **kwargs):
        nonlocal count
        count += 1
        print("{0} was called {1} times".format(fn.__name__, count))
    inner = wrap(fn)(inner)
    return inner
```

**\***

## 📖 Decorator with parameters (Decorator factory) {#decorator-with-parameters-decorator-factory heading="3"}

### \*Decorator with parameters\* are wrapper around existing decorators. Decorator returns \*closure\* but \*decorator with parameters\* returns decorator.

### A timer decorator with parameters

``` python
# name factory is decorator factory which accepts parameters
def factory(number):
    # name timer is actual decorator
    def timer(fn):
        from time import perf_counter

        # name inner is closure
        def inner(*args, **kwargs):
            total_time = 0
            for i in range(number):
                start_time = perf_counter()
                to_execute = fn(*args, **kwargs)
                end_time = perf_counter()
                execution_time = end_time - start_time
                total_time += execution_time
            average_time = total_time/number
            print('{0} took {1:.8f}s on an average to execute (tested for {2} times)'.format(fn.__name__, execution_time, number))
            return to_execute

        return inner
    return timer

@factory(50)
def function_1():
    for i in range(1000000):
        pass

@factory(5)
def function_2():
    for i in range(10000000):
        pass

function_1()
function_2()

```

## Recites {#recites-1 heading="3"}

### :HOWTO-RECITE:

Cover the notetaking column with a sheet of paper.  Then, looking at the
questions or cue-words in the question and cue column only, say aloud,
in your own words, the answers to the questions, facts, or ideas
indicated by the cue-words.

::: {.END .drawer}
:::

### main points

**\***

# Tuple {#tuple heading="2" id="650994bb-61c3-4e01-b5a0-e7eeda531610" collapsed="true"}

## \#[*wired fact*]{.spurious-link target="wired fact"} tuple is not created with `()` it is with `,` {#wired-fact-tuple-is-not-created-with-it-is-with collapsed="true"}

### `(1)` is not a tuple, it is a int, a single int of 1

### `1, ~ is a tuple
*** ~1, 2, 3` is a tuple

### `()` is used just to make code looks nicer

### create a empty tuple using `tuple()`, `()` will do as well

## Pack and unpack {#pack-and-unpack heading="3"}

### Similar to ((650504dd-7dea-4c1a-9a18-71aa0e1f2200))

### `a, b, c = 1, 2, 3`; `a, b, c = [1, 2, 3]`; `(a, b, c) = [1, 2, 3]` they works the same way

### behind the scenes: a, b, c is a `tuple`

### `a, b, c = 'XYZ'` `a='X', b='Y', c='Z'`

### `for e in 12, 10, 'hello'`

### swap: `a, b = b, a`

### #+BEGIN~SRC~ python {#beginsrc-python-4}

d = {\'1\': 1, \'2\':2} a, b = d \# a can be \'1\' or \'2\'

```{=org}
#+END_SRC
```
### extended unpack with `*` and `**` {#extended-unpack-with-and collapsed="true"}

1.  #+BEGIN~SRC~ python

    a, \*b = \[1, 2, 3\] \# a=1, b = \[2, 3\] a, \*b = \'XYZ\'
    #b=\[\'Y\', \'Z\'\] a, \*b, c = \'abcd\' \# b=\[\'b\', \'c\'\]

    ```{=org}
    #+END_SRC
    ```

2.  unpack can be used other way around

    ``` python
    l1=[1, 2]
    l2=[3, 4]
    l = [*l1, *l2]  # 1, 2, 3, 4
    l3 = 'XYZ'
    [*l1, *l3] # [1, 2, 'X', 'Y', 'Z']
    ```

3.  unpack dict with `**`

    1.  merge dict

        ``` python
        d1={1:1}
        d2={1:1, 2:2}
        d3={1:2: 3:3}
        d = {**d1, **d, **d3}  # duplicated value will be overwrote
        ```

4.  nested unpacking

    ``` python
    a, *b, (c, d, e) = [1, 2, 3, 'XYZ'] # b = [2, 3], c = X ...

    ```

5.  Ignore some of fields when unpack

    ``` python
    a, *_, c = (1, 2, 3, 4, 5)   # -> c = 5
    a, *ignore, c = (1, 2, 3, 4, 5)   # -> c = 5
    ```

## Named Tuple {#named-tuple heading="3"}

### namedtuple is a **class factory** return a subclass of tuple. You need a class~name~ and array of element names to create it. The name can also be a string of space \~ \~ or \~, \~ separated words

Syntax:

``` python
TupleClass = namedtuple(class_name, ['array', 'elements', 'string', 'format'])
TupleClass = namedtuple(class_name,  'string of names')
# Sample
Point = namedtuple('Point', ['x', 'y'])
# Now Point is a class
p1 = Point(1, 3)
print(p1.x, p1.y)
p1 = Point(x=1, y=3)
```

### Name tuple is tuple so it can use all tuple operations

``` python
x = Point[0]
x = Point[:1]
```

### Extend a tuple

``` python
Point1D = namedtuple('Point1D', ['x'])
fields = Point1D._field+('y',)
Point1D = namedtuple('Point2D', fields)
```

## Optimization {#optimization heading="3" collapsed="true"}

### Object Interning In Python

1.  Object interning is a technique used in Python to optimize memory
    usage and improve performance by reusing immutable objects instead
    of creating new instances. It is particularly useful for strings,
    integers and user-defined objects. By interning objects, Python can
    store only one copy of each distinct object in memory reducing
    memory consumption and speeding up operations that rely on object
    comparisons.

2.  Syntax:

    ``` python
    import sys
    interned_string = sys.intern(“string_to_intern”)
    interned_string2 = sys.intern(“string_to_intern”)
    interned_string is interned_string2 # faster than str cmp
    ```

3.  All identifiers are interned

### Peephole

1.  In Peephole optimization, Python optimizes code either by
    **pre-calculating** constant expressions or by **membership tests**
    (converting mutable data structures to immutable data structures.)

2.  [Peephole Optimization in
    Python](https://www.codesansar.com/python-programming/peephole-optimization.htm)

3.  Find what is pre-calculation by using

    `your_obj.__code__.co_consts` **\*\***

#  [[PROPERTIES]{.smallcaps}]{.tag tag-name="PROPERTIES"} {#section-3}

:query-table: false

::: {.END .drawer}
::: QUERY
{:title \[:b \"Page items\"\] :query \[:find (pull ?b \[\*\]) :in \$
?parent % :where \[?p :block/name \"javascript\"\] ;lower-case page name
\[?b :block/refs ?p\] (check-parent ?b ?parent) \] :rules \[
\[(check-parent ?b ?parent) \[?b :block/parent ?parent\] \]
\[(check-parent ?b ?parent) \[?b :block/parent ?c\] (check-parent ?c
?parent) \] \] :group-by-page? false :breadcrumb-show? false :inputs
\[:parent-block\] }
:::
:::

\* \*
