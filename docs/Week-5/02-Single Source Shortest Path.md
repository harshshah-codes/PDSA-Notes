# Single Source Shortest Path

By single source shortest path, we mean that we need to find the shortest path from a **specific source vertex** to all other vertices.

We can achieve the solution in two ways.

## Djikstra's Algorithm
### Algorithm
1. Initialize an empty $n\ \text x\ n$ matrix and in the first column set the distance  of the source vertex to be $0$ and rest other vertices to $\infin$

2. Find the vertex $v$ with the least distance $d.$ Mark $v$ as visited.

3. Check the neighbours of $v$ and check whether they are unvisited. If the neighbout is not visited, then check for $d[v]+W<d[n].$ If it is the case, then assign this value to $d[n].$ 

4. Repeat steps (3) and (4) for all the unvisited vertices.

### Visual Representation
<iframe src="https://visualgo.net/en/sssp" frameborder="0" height="700px" allowfullscreen="true"> </iframe>