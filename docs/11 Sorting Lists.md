# Sorting Lists

## Selection Sort

### Algorithm

- Go through the list and find the smallest element and swap it with the first element.
- Next go through the rest of the list and find the smallest element and swap it with the second element.
- An so on...

### Code

```python linenums="1"
def SelectionSort(L):
    n = len(L)
    if n < 1:
        return L

    for i in range(n):
        mpos = i
        for j in range(i+1, n):
            if L[j] < L[mpos]:
                mpos = j
        L[i], L[mpos] = L[mpos], L[i]

    return L
```

### Efficiency

- Outer loop takes $n$ steps
- Inner loop takes $n - i$ steps
- $T(n) = n + (n-1)+(n-2) +\dots +1 = \cfrac{n(n+1)}2$
- Hence, $T(n) = O(n^2)$

## Insertion Sort

### Algorithm

#### Approach 1

- Take the first element of the list and add it to a new list.
- Take the next element of the list and add it to list in such a way that the list remains sorted.
- Again take the next element of the list and add it to list in such a way that the list remains sorted.
- Repeat this until the orignal list is empty.

#### Approach 2

- Take the second element of the list and see if the element is smaller than the first element. If it is set the element to occupy the first position and push the list forward. If it is not leave the element and continue to next element.
- Now check whether the element is smaller than the any of the previous elements. If it is set the element to the correct position and push the list forward. If it is not leave the element and continue to next element.
- Repeat the steps until the list is empty.

### Code

```python linenums="1"
def InsertionSort(L):
    n = len(L)
    if L < 1:
        return L
    for i in range(n):
        j = i
        while (j > 0) and (L[j] < L[j - 1]):
            L[j], L[j - 1] = L[j - 1], L[j]
            j -= 1

    return L
```

### Efficiency

- Outer loop takes $n$ steps
- Inner loop takes $i$ steps to insert `L[i]` into `L[:i]`
- $T(n) = 0 + 1 + ... (n-1) = \cfrac{n(n-1)}2$
- Hence, $T(n) = O(n^2)$

## Merge Sort

### Approach

- Divide the list into two halves
- Seprately sort the two halves, say `A` and `B`.
- Now compare the first elements of `A` and `B` and add the smaller element to the new list.
- Repeat untill the end of both the lists.

!!! tip

    We use the principle of **divide and conquer** to solve the problem.

### Code

``` python linenums="1"
def merge(A, B):
    m, n = len(A), len(B)
    C, i, j, k = [], 0, 0, 0
    while k < m+n:
        if i == m:
            C.append(B[j: ])
            k += (n - j)
        elif j == n:
            C.append(A[i:])
            k += (m - i)
        elif A[i] < B[j]:
            C.append(A[i])
            i += 1
            k += 1
        else:
            C.append(B[j])
            j += 1
            k += 1
    return C

def mergeSort(L):
    n = len(L)

    if n <= 1:
        return L

    left = mergeSort(L[:n//2])
    right = mergeSort(L[n//2:])

    B = merge(left, right)

    return B
```

### Efficiency

- In the worst case, the loop in `merge` function runs $m+n$ times.
- Hence `merge` function takes $O(m+n)$ time.
- We know that, $O(m+n) = O(2(\max(m, n)))$. But since here $m\approx n$, hence the `merge` takes $O(n)$ time.
- Now let $n$ be the input size for `mergeSort`. And also $n=2^k$.
- We can see that $T(0) = T(1) = 1$ and $T(n) = 2T(n/2) + n$, where $n$ is the time required to merge the two arrays.
- Using `unwind and solve` we get, $T(n)=2^kT(\cfrac{n}{2^k})+kn$
- Now since $k=\log(n)$, $T(n) = n + n\log(n)$
- Hence $T(n) = O(n\log(n))$

## Quick Sort

### Approach

- Select an element known as `pivot` and split the list with respect to the `pivot` say `m`.
- Then move all values $\leq m$ to the left of `L` and the values $\geq m$ to the right of `L`.
- Then we recursively sort both the halves.

### Code

```python linenums="1"
def quickSort(L, l, r):
    if (r - l == 1):
        return L

    pivot, lower, upper = L[l], l+1, l+1

    for i in range(l+1, r):
        if L[i] > pivot:
            upper += 1
        else:
            L[i], L[lower] = L[lower], L[i]
            lower, upper = lower + 1, upper + 1
    L[l], L[lower-1] = L[lower-1], L[l]
    lower = lower - 1

    quickSort(L, l, lower)
    quickSort(L, lower + 1, upper)

    return L

```

### Efficiency

- Partition with respect to `pivot` takes $O(n)$ time.
- For the worst case, `pivot` is maximum or minimum, i.e. partitions are of sizes $0 \text{ and } n-1$
- $T(n) = T(n-1) + n = O(n^2)$
- Worst case for quicksort is an array that is already sorted.
