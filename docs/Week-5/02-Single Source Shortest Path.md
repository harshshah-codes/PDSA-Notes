# Single Source Shortest Path

By single source shortest path, we mean that we need to find the shortest path from a **specific source vertex** to all other vertices.

We can achieve the solution in two ways.

## Djikstra's Algorithm
### Algorithm
1. Initialize an empty $n\ \text x\ n$ matrix and in the first column set the distance  of the source vertex to be $0$ and rest other vertices to $\infin$

2. Find the vertex $v$ with the least distance $d.$ Mark $v$ as visited.

3. Check the neighbours of $v$ and check whether they are unvisited. If the neighbout is not visited, then check for $d[v]+W<d[n].$ If it is the case, then assign this value to $d[n].$ 

4. Repeat steps (3) and (4) for all the unvisited vertices.

### Implementation
#### Using a NumPy Array

```python linenums="1"
def DjikstraAlgorithm(adj, source):
    rows, cols, x = adj.shape
    visited = {k: False for k in adj[rows]}
    distance = {k: float('inf') for k in adj[rows]}

    distance[source] = 0

    for u in range(rows):
        next_dist = min([distance[v] for v in range(rows)
                           if not visited[v]
                        ])
        next_vertex_list = [v for v in range(rows)
                              if not visited[v]
                              and distance[v] == next_dist 
                           ]

        if not next_vertex_list:
            break

        next_vertex = min(next_vertex_list)
        visited[next_vertex] = True
        for i in range(cols):
            if (adj[next_vertex, i, 0] == 1) and (not visited[i]):
                if dist[i] > adj[next_vertex, i, 1] + next_dist:
                    dist[i] = adj[next_vertex, i, 1]

    return distance 

```

#### Using an Adjacency List

```python linenums="1"
def DjikstrasAlgorithm(adjList, source):
    vertices = len(adjList.keys())
    visited = {k: False for k in range(vertices)}
    distance = {k: float('inf') for k in range(vertices)}

    distance[source] = 0

    for i in adjList:
        next_dist = min([distance[v] for v in adjList 
                                        if not visited[v]
                        ])
        next_vertex_list = [v for v in adjList 
                                if not visited[v]
                                and distance[v] == next_dist
                           ]

        if not next_vertex_list:
            break

        next_vertex = min(next_vertex_list)
        visited[next_vertex] = True

        for v in adjList:
            for neighbour, weight in v:
                if weight + next_dist < distance[neighbour]:
                    distance[neighbour] = weight + next_dist

    return distance 
```

### Time Complexity
The time complexity for **Djikstra's Algorithm** in either of the two cases is $O(n^2).$ 

You can minimise this using **Heaps** as discussed in further articles.

!!! danger

    **Djikstra's Algorithm** does not allow the presence of negative edge weights in the graph.

## Bellman-Ford Algorithm
**Bellman Ford Algorithm** is an algorithm to find Single Source Shortest Paths similar to the [Djikstra's Algorithm](#djikstras-algorithm) except the fact that it allows the use of ***negative edge weights*** but not a ***negative cycle***.

### Algorithm
1. Initialise a dictionary $D$ that stores the distance and $D(v) = \begin{bmatrix}0 \text{, If v is source vertex}\\ \infin \text{, otherwise}\end{bmatrix}$
2. Pick a vertex $j$ that has an edge $(j,k)$ and set $D(k) = min(D(k), D(j)+\text{weight}(j, k))$
3. Repeat the step $2$ for $n-1$ times.

### Implementation
#### Using Numpy Array
```python linenums="1"
def BellmanFord(adj, source):
    rows, cols, x = adj.shape
    distance = {k: float('inf') for k in range(rows)}

    distance[source] = 0

    for i in range(rows):
        for u in range(rows):
            for j in range(cols):
                if adj[i, j, 0] == 1:
                    distance[j] = min(distance[j], distance[i] + adj[i, j, 1])

    return distance
```

#### Using Adjancency List
```python linenums="1"
def BellmanFord(adj, source):
    vertices = len(adj.keys())

    distance = {k: float('inf') for k in range(vertices)}
    distance[source] = 0

    for i in adj:
        for u in adj:
            for vertex, dist in adj[u]:
                distance[vertex] = min(distance[vertex], distance[u] + dist)

    return distance

```

### Time Complexity
- Using the [numpy method](#using-numpy-array) the time complexity is $O(n^3)$
- Shifting to the [Adjacency List](#using-adjancency-list) the time complexity becomes $O(mn),$ where $m$ is the number of edges and $n$ is the number of vertices.

## Visualisation of Single Source Shortest Path Algorithms
<iframe src="https://visualgo.net/en/sssp" frameborder="0" height="700px" width="650px" allowfullscreen="true"> </iframe>

