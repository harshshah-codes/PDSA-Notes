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

### Example-4(Count number of bits in binary representation of a number `n`)

```python linenums="1" title="no_of_bits.py"
def countBits(n):
    count = 1
    while n > 1:
        count += 1
        n //= 2
    return count
```

- This problem takes $\log(n)$ steps to reach $1$ from $n$.
