# Heaps

The heaps are tree implementations of the [**Priority Queues**](./02%20Priority%20Queues.md)

A heap is basically a [Binary Tree](../Extras/01%20Binary%20Trees.md) with some more constraints.

## Constraints
- **Structural Constraint**: The binary tree must be filled level by level, i.e., before completing level $n-1$ you cannot move to level $n.$

- **Constraint on values**: For the *max-heap*, the children of each node must be **either less than or equal to the parent node** and for the *min-heap*, the children of each node must be **either greater than or equal to the parent node**. 

- By the previous property, the root of the *max-heap* is the greatest element, and the root of the *min-heap* is the least element.

## Strategy

Now the priority queue requires two main functions, 
- `insert(n)`
- `delete_max()` or `delete_min()`

So, this topic focuses on how are we to implement this functions,

### `insert(n)` 
1. Add a new node, using the [structural constraint](#constraints) of the heap and set the value of node to be `n`.
2. Now check whether the node satisfies the [value constraint](#constraints) and if not, swap the parent and the child node.
3. Repeat $(2)$ by following the path to the root until the value constraint is satisfied.


### `delete_max()` or `delete_min()`
Let us consider the case of a *max-heap*, 

So the maximum value of the tree will be the **root** of the tree.

Now due to the **structural constraint** of the root, the node removed will be the last node of the tree. Doing so, the value of the last node will have no node to sit on.

So what we do is take the value of the deleted node and set it as the value of **root node** and then do the steps, i.e., comparing the root with both child node and swapping it with the bigger child, until the **value constraint** of the heap is satisfies.

## Implementation
### Storing the tree
Consider the heap, 
![Heap](../assets/Implementation%20of%20Heap.png)

Store the heap as a list, i.e., `heap=[h0,h1,h2...h9]`. 

If you tinker upon the heap, you'll find that, children of `H[i]` will be `H[2i+1]`, `H[2i+2]` and the parent of `H[i]` will be `H[(i-1)//2]`

### Building a heap from a list (`heapify()`)
#### Simple approach
One thing you can do, is start with an empty heap and do `insert(element_from_list)` repeatedly into the heap.

The cost of this function is $O(N\log(N))$ for $N$ inserts

#### A better approach
If you consider a list, and consider it's leaf nodes, you will find that the leaf nodes are already satisfying the heap properties.

And the number of leaf_nodes will be `n//2`, where `n` is the number of nodes

So what you can do is start from the bottom of the list to be considered as heap, and start fixing it from the bottom, you will see that you can fix the whole list in $O(n)$

### `insert(n)`


## Time Complexity
### `insert(n)`

Consider a *max-heap*, then for a `n`, such that $n>$ (the root value), there will be comparisons equal to the height of the tree, hence the complexity of inserting a node will be $O(\text{Height of the tree})=O(\log(N)),$ where $N$ is the number of nodes in the tree

### `delete_max() or delete_min()`

If you ponder upon the function, you can see that we follow only a single path, hence the complexity of deleting the root node will be $O(\text{Height of the tree})=O(\log(N)),$ where $N$ is the number of nodes in the tree.