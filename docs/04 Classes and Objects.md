# Classes and Objects

To understand classes, we first need to know about **abstract datatype**.



### Abstract Datatype

Let us consider an implementation of **Stack** in python language.&#x20;

We see that the **Stack** implementation itself gives functions to manipulate data, eg. `push() `or `pop()` and the implementation is private.

So basically, an abstract datatype:

* Stores some data.
* Provides designated functions to manipulate data.
* &#x20;Separates the (**private**) implementation and the (**public**) specification

### Class

A implementation of is [**Abstract Datatype**](#abstract-datatype) a class**.**

A class is basically a:

* Template for a user defined datatype.
* How data is stored
* How public functions manipulate the data

### Object

An object is an instance of a class.

### Class as a real-world example

#### 2D Points

A class created in python always needs to have the \`\_\_init\_\_()\` function. It is a special function and is known as **constructor**. The only objective of the **constructor** is to initialise the data members of a class a default value.

> Each function of a class accepts a compulsory parameter known as `self`. It contains the a particular instance of a class to be worked upon.&#x20;

```py linenums="1"
class Point:
  def __init__(self, a = 0, b = 0):
    self.x = a
    self.y = b
```

Let us define another function called translate that shifts the point $(x,y)$ by $(\Delta x, \Delta y)$.

```py linenums="1"
def translate(self, deltax, deltay):
  self.x += deltax
  self.y += deltay
```

Let us define another function that gets us the distance of the point from origin using the formula $d=\sqrt{x^2+y^2}$

```py linenums="1"
def odistance(self):
  d = ((x ** 2) + (y ** 2)) ** (0.5)
  return d
```



Therefore the whole class `Point` is as follows:

```py linenums="1"
class Point:
  def __init__(self, a = 0, b = 0):
    self.x = a
    self.y = b

  def translate(self, deltax, deltay):
    self.x += deltax
    self.y += deltay

  def odistance(self):
    d = ((x ** 2) + (y ** 2)) ** (0.5)
    return d
```




### Special Class functions

| Function name |                                                    Use                                                   |
|:-------------:|:--------------------------------------------------------------------------------------------------------:|
|   _\_init__()  |                                                Constructor                                               |
|   _\_str__()   | Converts object to string.  - It is implicitly called by `print` as print can only be used with strings. |
|   _\_add__()   |                                         Implicitly called by `+`                                         |

Similarly there are many more functions such as `__mult__()` for multiplication, `__le__()` for less than operator and so on.