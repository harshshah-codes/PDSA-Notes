# Comparing Orders of Magnitude

This section deals with how to compare two functions based on their orders of magnitude.

## Big-O Notation(Upper Bounds)

$f(x)$ is said to be **$O(g(x))$** if there exists two constants $c$ and $x_0$ such that the function $c.g(x)$ is an **upper bound** for $f(x)$ beyond $x_0$.

Mathematically,

$$
f(x) \leq c.g(x), \text{for every } x\geq x_0
$$

!!! warning

    There can be more than a pair of $x_0$ and $c$ for every algorithm.

### Properties of Big-O Notation

#### Addition of two functions

The addition of two functions lies below the **maximum** of the two functions in terms of **Big-O** notation.

$$
\text{Let }f_1(n)\text{ is }O(g_1(n)) \\ \ \\ \text{and }f_2(n)\text{ is }O(g_2(n))\\ \ \\ \text{then } f_1(n)+f_2(n)\text{ is }O(max(g_1(n), g_2(n))).
$$

!!!tip

    The upper bound of any algorithm is given by the **least efficient phase** of the algorithm.

## $\Omega$ notation(Lower Bounds)

$f(x)$ is said to be **$\Omega(g(x))$** if there exists two constants $c$ and $x_0$ such that the function $c.g(x)$ is a **lower bound** for $f(x)$ beyond $x_0$.

Mathematically,

$$
f(x) \geq c.g(x), \text{for every } x\geq x_0
$$

!!! note

    Typically we establish lower bounds for whole problem as a whole, rather than each algorithm of it.

## $\Theta$ notation(Tight Bounds)

$f(x)$ is said to be **$\Theta(g(x))$** if there exists three constants $c_1,c_2$ and $x_0$ such that the function $c_1.g(x)$ is a **lower bound** for $f(x)$ beyond $x_0$ and $c_2.g(x)$ is an **upper bound** for $f(x)$ beyond $x_0$.

$$
c_1.g(x) \leq f(x) \leq c_2.g(x), \text{for every } x\geq x_0
$$
