# All Pair Shortest Paths

Sometimes it is needed to find shortest path from each vertex to each vertex. 

For example, when laying railway lines it is important to find the shortest routes between pair of two cities.

One of the ways to approach this problem is by running the [single source shortest path algorithms](./02-Single%20Source%20Shortest%20Path.md) on each and every node.

But this is not efficient.

This brings [**Floyd Warshall's algorithm**](#floyd-warshalls-algorithm) into the picture.

But before that we need to know about [**Warshall's Algorithm**](#warshalls-algorithm)

## Warshall's algorithm
Consider a case where there is an edge from vertex $i$ to $k,$ i.e., $i\to k.$ And there also exists a vertex from $j$ to $k,$ i.e. $j\to k.$

Now because of this, I can reach $j$ from $i$ after travelling through the intermediate node $k,$ i.e., $i\to k\to j.$

## Some Special Notations
Consider B is a matrix, such that $B[i][j]$ is $1$ if there exists a path between the vertex $i$ and $j$

Now we denote all this cases using some special notations:
- $B^0[i,j] = 1 \leftrightarrow$ there exists a direct edge from $i$ to $j.$
- $B^1[i,j] = 1 \leftrightarrow$ there exists a edge from $i$ to $j$ with maximum $1$ intermediate node in between.
- Similarly, $B^k[i,j] = 1 \leftrightarrow$ there exists a edge from $i$ to $j$ with maximum $k$ intermediate nodes in between

## Floyd Warshall's Algorithm
### Algorithm
1. Let us define a $n\text{ x }n$ matrix named $SP,$ where $n$ is the number of vertices.
2. Initialise $SP^0[i,j]=W[i,j],$ if there exists a direct edge from $i$ to $j$ and the weight of the edge is $W[i,j].$
3. If there does not exist a direct edge between $i$ and $j$ set $SP^0[i,j] = \infin$
4. Now $SP^{k+1}[i,j] = \min(SP^k[i,j], SP^k[i,k]+SP^k[k,j])$ 
5. Repeat step $4$ for n times.
6. Now $SP^n[i,j]$ contains the shortest distance between $i$ and $j$

### Implementation
```python linenums="1"
def FloydWarshall(adj):
    rows, cols, x = adj.shape

    SP  = np.zeroes(shape=(rows, cols, cols+1))

    for row in range(rows):
        for col in range(cols):
            SP[row, col, 0] = float('inf')

    for row in range(rows):
        for col in range(cols):
            if adj[row, col, 0] == 1:
                SP[row, col, 0] = adj[row, col, 1]

    for k in range(cols + 1):
        for row in range(rows):
            for col in range(cols):
                SP[i, j, k] = min(SP[i, j, k], SP[i, k-1, k-1] + SP[k-1, j, k-1] ) 
    
    return SP[:,:,cols]
```

### Time Complexity
This implementation has the time complexity of $O(n^3)$