# Topological Sorting

Topological sorting can only be done in **Directed Acyclic Graphs (DAGs)**.

It is a linear ordering of vertices such that for every directed edge $u \rightarrow v$, vertex $u$ comes before $v$ in the ordering.

## Steps to accomplish Topological Sort

1. Find the indegree of each node of the graph.
2. Put the nodes with indegree $0$ inside the **Queue**.
3. Now remove the first element of the **Queue**, add it to the **result list** and remove the node along with its corresponding edges from the graph.
4. Repeat steps $1,\ 2$ and $3$ until the **Queue** is empty.
