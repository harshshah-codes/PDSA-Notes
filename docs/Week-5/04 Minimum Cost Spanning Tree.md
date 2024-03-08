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

### Implementation
#### Basic Implementation
```python linenums="1"
def Primsalgorithm(adjList):
    visited = {k: False for k in adjList}
    distance = {k: float('inf') for k in adjList}
    tree = []

    visited[0] = True

    for vertex, dist in adjList[0]:
        distance[vertex] = dist

    for i in adjList:
        mindist = float('inf')
        nextv = None

        for ver, dist in adjList[i]:
            if (visited[i]) and (not visited[ver]) and (dist < mindist):
                mindist = dist
                nexte = (i, ver)
                nextv = ver

        if not nextv:
            break

        visited[nextv] = True
        tree.append(nexte) 

        for ver, dist in adjList[nextv]:
            if not visited[ver]:
                distance[ver] = min(distance[ver], dist)

    return tree
```

#### A Better Approach
```python linenums="1"
def Primsalgorithm(adjList):
    visited, distance = {}, {}
    neighbour = {}
    
    for k in adjList:
        visited[k] = False
        distance[k] = float('inf')
        neighbour[k] = -1

    visited[0] = True
    for ver, dis in adjList[0]:
        distance[ver] = dis
        neighbour[ver] = 0

    for i in range(1, len(adjList)):
        nextd = min([distance[v] for v in adjList if not visited[v]])

        next_vertex_list = [v for v in adjList if (not visited[v]) and (nextd == distance[v])]

        if not next_vertex_list:
            break

        next_vertex = min(next_vertex_list)
        visited[next_vertex] = True

        for ver, dis in adjList[next_vertex]:
            if not visited[ver]:
                distance[ver] = min(distance[ver], dis)
                neighbour[ver] = next_vertex

    return neighbour
```

### Time Complexity
#### Basic Implementation
The time complexity of the [basic implementation](#basic-implementation) is $O(n^3)$

#### Approach inspired by Djikstra's Algorithm
The [second approach](#a-better-approach) is inspired by the [Djikstra's Algorithm](./02-Single%20Source%20Shortest%20Path/#djikstras-algorithm). 

This implementation has the time complexity of $O(n^2)$ similar to that of **Djikstra's Algorithm**

## Kruskal's Algorithm