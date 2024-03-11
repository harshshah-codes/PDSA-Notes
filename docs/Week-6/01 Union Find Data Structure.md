# Union Find Data Structure

The Union Find data structure has mainly 3 operations:
- MakeUnionFind($S$) - set up singleton components $s, s\in S$
- find($s$) - find the component that contains element $s$ 
- union($s,s'$) - merge two components $s$ and $s'$

## Basic Setup (or Notations)
Let us consider a set $S$ partitioned into the components $\{c_1,c_2,...c_j\}$ with only a single element $s\in S,$ i.e., each $s$ belongs to a single component

## Implementation
### Naive Implementation
- Let us assume $S=\{0,1,2,...,n-1\}$
- Create a dictionary `component`

- Now for the function `MakeUnionFind(S)` - Set `component[i] = i` for each $i\in S$

- For the function `find(i)` - return `component[i]`
- And for the function `union(i, j)` - set all the $s$ from the component $i$ to $j$

```python linenums="1"
class UnionFind:
    def __init__(self):
        self.component = {}

    def MakeUnionFind(self, S):
        self.component = {i: i for i in S}
        self.n = len(S)

    def find(self, i):
        return self.component[i]

    def union(self, i, j):
        c_old = self.components[i]
        c_new = self.components[j]
        for k in range(self.n):
            if component[k] == c_old:
                component[k] = c_new

```

### A better Implementation
As we saw above, the `union` function was inefficient. 

So to improve that, we could create two more dictionaries `members` and `sizes`, where `members[c] = list of all members of the component c` and `sizes[c] = len(members[c])`

```python linenums="1"
class UnionFind:
    def __init__(self):
        self.component = {}
        self.members = {}
        self.sizes = {}

    def MakeUnionFind(self, S):
        for i in S: 
            self.component[i] = i
            self.members[i] = [i]
            self.size[i] = 1
        self.n = len(S)

    def find(self, i):
        return self.component[i]

    def union(self, i, j):
        c_old = components[i]
        c_new = components[j]

        if self.size[c_old] > self.size[c_new]:
            return union(self, j, i)

        for k in members[i]:
            self.components[k] = c_new
            self.members[j].append(k)
            self.size[c_new] += 1
        
        self.members[i] = []
        self.size[c_old] = 0

```

## Time Complexity
### [Basic Implementation](#naive-implementation)
The time complexity of the funtions are:
-  `MakeUnionFind` - $O(n)$
- `find(i)` - $O(1)$
- `union(i,j)` - $O(n)$

### [A Better Implementation](#a-better-implementation)
The time complexity of the funtions are:
-  `MakeUnionFind` - $O(n)$
- `find(i)` - $O(1)$
- `union(i,j)` - $O(\text{size(Smaller Set)})$
- Average Cost of $m$ `union` operations - $O(m\log m)$