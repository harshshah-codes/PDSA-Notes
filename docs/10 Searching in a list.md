# Searching in a list

## Naive Approach

- Scan the whole list for the element required.
- Worst case is when the element is not present in the list.
- Worst case time complexity is $O(n)$, where $n$ is the size of the input list.

```python linenums="1"
def naiveSearch(L, k):
    for i in L:
        if i == k:
            return True
    return False
```

## Binary Search Approach

- The only condition for binary search is that the **list should be sorted**.

### Approach

- Let `k` be the element to be searched and the list to be sorted in **ascending order**.
- Compare `k` with the mid point of the list.
- If it matches, return `True`
- If the mid value is $>$ `k`, then search the first half, else search the second half.
- Stop when the interval to be searched becomes empty

```python linenums="1"
def binarySearch(L, k):
    beg, end = 0, len(L)
    while beg != end:
        mid = (beg + end) // 2
        if L[mid] == k:
            return True
        if L[mid] < k:
            beg = mid + 1
        else:
            end = mid - 1
    return False
```

- This apprach takes $\log(n)$ time to search for an element at a worst case scenario.

## Activity

Implement the binary search algorithm using **recursion**
