# Minimum Cost Spanning Tree
Sometime there may arise a case that we want to limit cost on a resource but want the graph to remain well-connected.

For example, suppose a fiber connection company wants to connect $n$ cities and they want to use the lowest amount of **optic cable** to be utilised.

The solution to this kind of problems is **Minimum Cost Spanning Tree**. 

!!! tip Fact to Know

    A minimally connected graph is called a **Spanning tree**.

## Important Notes on Spanning Trees
1. Removing an edge from the tree disconnects a graph
2. Adding an edge to the tree forms a loop.
3. There can be more than one spanning tree for a graph
4. A tree on $n$ vertices has exactly $n-1$ edges
5. In a tree, each vertex is joined by a unique path.


!!! warning Remember

    We choose the spanning tree with minimum cost to solve the problem discussed at the start of the page.


Now to create or find a **minimum cost spanning tree**, there are two algorithms,
- [**Prim's algorithm**](#prims-algorithm)
- [**Kruskal's Algorithm**](#kruskals-algorithm)

## Prim's Algorithm

### Algorithm
1. Consider two sets $TE$ and $TV,$ representing **tree edges in MCST** and **tree vertices in MCST** respectively.
2. Initially, $TV=TE=\phi$
3.  Suppose we find an edge $e$ with the lowest weight in the entire graph and it connects edges $i$ and $j.$
4. Now $TV$ becomes $\{i,j\}$ and $TE$ becomes $\{e\}$
5. Now find an edge $t$ connecting vertices $v_1$ and $v_2$ such that it has the minimum weight and $v_1\in TV$ and $v_2 \notin TV.$
6. Now add $v_2$ in $TV$ and $t$ in $TE.$
7. Repeat steps $5$ and $6$ for $n-2$ times

<!-- ### Implementation
#### Using Adjacency List
```python linenums="1"
def Primsalgorithm(adjList):
    visited, edges = {k: False for k i }, {}
    tree = []

    min_weight = min(adj)
```

## Kruskal's Algorithm -->