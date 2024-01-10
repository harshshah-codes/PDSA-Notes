# Revisiting Python

## Some common programs

#### Computing "GCD" for two numbers `m` and `n`.

```py title="Approach 1" linenums="1"
def gcd(m, n):
    # List of common factors of m and n
    cf = []
    for i in range(1, min(m, n) + 1):
        if (m%i == 0) and (n%i == 0):
          cf.append(i)

    return (cf[-1])
```

```py title="Approach 2" linenums="1"
def gcd(m, n):
  # List of common factors of m and n
  mrcf = 1
  for i in range(1, min(m, n) + 1):
      if (m%i == 0) and (n%i == 0):
        mrcf = i

  return (mrcf)
```

Here both the codes are proportional to `min(m, n)`

##### Recursive Approach

$$
\text{Let } d \text { divides } m \text{ and } n.\\
m = ad, n = bd\\
\text{Now, } m - n = (a - b)d
$$

Therefore, d also divides `m` and `n`
Using this we can also apply recursion to solve the GCD problem

```py linenums="1" title="Recursive-GCD.py"
def rec_gcd(m, n):
  a, b = max(m, n), min(m, n)
  if (a % b == 0):
    return b
  else:
    return (rec_gcd(a, a-b))

```

##### Euclid's algorithm

Suppose `n` does not divide `m`
Then, let $m = nq + r ... (1)$
Also, let $m =ad, n = bd ... (2)$
Therefore eqn($1$) becomes $ad + (bd)q + r$. This means that $r$ is of a form $cd$.

Now the recursive function becomes:

- Base case: m % n == 0, return n
- Recursive case: if m % n != 0, return gcd(m, m % n)

```py linenums="1" title="Optimised-GCD.py"
def opt_gcd(m, n):
  a, b = max(m, n), min(m, n)
  if (a % b == 0):
    return b
  else:
    return (opt_gcd(a, a % b))

```

#### Checking prime numbers

```py linenums="1" title="factors.py"
def factors(n):
  f1 =[]
  for i in range(1, n+1):
    if n%i == 0:
      f1.append(i)

  return f1
```

```py linenums="1" title="primes-approach-1.py"
def prime(n):
  return (factors(n) == [1, n])
```

```py linenums="1" title="primes-approach-2.py"
def prime(n):
  return (len(factors(n)) == 2)
```

##### Listing primes upto `m`

```py linenums="1" title="primes-upto-m.py"
def primes_upto_m(m):
  pr = []
  for i in range(1, m+1):
    if prime(i):
      pr.append(i)

  return pr
```

##### Listing first `m` primes

```py linenums="1" title="first-m-primes.py"
def first_m_primes(m):
  pr = []
  i = 1
  while (len(pr) < m-1):
    if prime(i):
      pr.append(i)
    i += 1

  return pr
```

|                        For                         |                              While                              |
| :------------------------------------------------: | :-------------------------------------------------------------: |
| When you know the number of iterations in advance. | When you are not sure about the number of iterations in advance |

#### Computing primes without using maintaining factors lists

```py linenums="1" title="prime-using-for-loop.py"
def prime(m):
  flag = True
  for i in range(2, n):
    if m%i == 0:
      flag = False
      break

  return flag
```

```py linenums="1" title="prime-using-while-loop.py"
def prime(m):
  flag = True
  i = 2
  while (flag && i < n)
    if m%i == 0:
      flag = False
      break
    i += 1

  return flag
```

##### Optimising prime function

We know that $\sqrt m$ is the middle factor of $m$.
Also factors occurs in pairs.

So we can use this concept to check for primes with the limits to be `2` to $\sqrt{m}$ instead of `2` to `m`

```py linenums="1" title="optimised-prime.py"
def prime(m):
  flag = True
  for i in range(2, int(n ** 0.5) + 1):
    if m%i == 0:
      flag = False
      break

  return flag
```

#### Assignments to try out

##### Twin primes

Two prime numbers with their absolute difference to be 2 are called twin primes. Mathematically speaking, if $m$ and $m+2$ are primes then $m$ and $m+2$ are twin primes.

