# Calculating complexity

## Iterative Programs

### Example-1 (Maximum from a list)

Consider the following function

```python linenums="1" title="max_list.py"
def max_elem(L):
    max_val = L[0]
    for i in L:
        if i > max_val:
            max_val = i

    return max_val
```

- **Input size** is the length of `L`.
- Always take `n`, i.e., length of `L` steps to complete.
- Worst case Complexity is $O(n)$.

### Example-2 (Check whether the loop has duplicates)

```python linenums="1" title="duplicates_in_list.py"
    def hasDuplicates(L):
        n = len(L)
        for i in range(n):
            for j in range(i+1, n):
                if L[i] == L[j]:
                    return False
        return True
```

- **Input size** is len of `L`, i.e., `n`
- **Worst case** is that no duplicates exist and both the loops execute completely.
- Time is $(n-1)+(n-2)+(n-3)+\dots+1=\cfrac{n(n-1)}{2}$
- Worst case complexity is $O(n^2)$

### Example-3 (Matrix Multiplication)

```python linenums="1" title="matrix_multiplication.py"
def multiply(A, B):
    m, n, p = len(A), len(B), len(B[0])

    C = [[0 for i in range(p)]
        for j in range(m)]

    for i in range(m):
        for j in range(p):
            for k in range(n):
                C[i][j] += A[i][k] * B[k][j]

    return C
```

- **Input size**: Input matrices has the size $m \text{ x } n,n\text{ x }p$.
- Output matrix is $m\text{ x }p$.
- Overall time is $O(mnp)$, i.e., $O(n^3)$, if $m = p = n$.

### Example-4 (Count number of bits in binary representation of a number `n`)

```python linenums="1" title="no_of_bits.py"
def countBits(n):
    count = 1
    while n > 1:
        count += 1
        n //= 2
    return count
```

- This problem takes $\log(n)$ steps to reach $1$ from $n$.

!!! tip Note

    For number theoretic problems, input size is the number of digits in the number.

## Recursive Programs

### Example-1 (Towers of Hanoi)

Tower of Hanoi is a mathematical puzzle where we have three rods (A, B, and C) and N disks. Initially, all the disks are stacked in decreasing value of diameter i.e., the smallest disk is placed on the top and they are on rod A. The objective of the puzzle is to move the entire stack to another rod (here considered C), obeying the following simple rules:

- Only one disk can be moved at a time.
- Each move consists of taking the upper disk from one of the stacks and placing it on top of another stack i.e. a disk can only be moved if it is the uppermost disk on a stack.
- No disk may be placed on top of a smaller disk.

> Read more about [Towers of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi).

To solve this problem we use a recursive approach. You can learn more about the approach from the [Proffessor's video](https://www.youtube.com/watch?v=L1SPxZvjpoM&t=626s).

#### Approach

- Let the initial peg be `A`, final peg be `B` and transit peg be `C`.
- Move $n-1$ discs from from peg `A` to `C`.
- Then move the last disc from `A` to `B`.
- Now `C` has $n-1$ discs and `B` has 1 disc.
- Now move $n-2$ discs from `C` to `A`. And the last disc from `C` to `B` and so on.

$$
\text{Now let } M(n) - \text{ Number of moves to move }n\text{ discs and }M(1)=1.
\\\ \\ \text{So, using the recursive approach, }\\\ \\M(n) = M(n-1)+M(1)+M(n-1) = 2M(n-1)+1
$$

Similarly if you unwind the $M(n-1)$ and so on, then $M(n) = 2^{n-1}+(2^{n-1}-1) = 2^{n-1}$

<iframe width="1080" height="600" src="https://www.youtube.com/embed/L1SPxZvjpoM?start=626" title="W2L3_Calculating Complexity - Examples" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
