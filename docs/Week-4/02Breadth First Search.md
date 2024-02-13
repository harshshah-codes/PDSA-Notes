# Breadth First Search (BFS)

BFS is a graph traversal algorithm that starts traversing the graph from the root node and explores all the neighbouring nodes at the same depth. Then, it selects the nearest node and explores all the unexplored nodes. The algorithm follows the same process for each of the nearest nodes until it finds the goal.

We use the data structure **queue** to implement BFS.

## Algorithm

- **Step 1**: Choose the **root** node and add it to the queue.
- Step 2: Mark it as visited. (You can make a **list** named `visited` to keep track of the visited nodes.)
- **Step 3**: Now remove the element you are currently in from the queue and add all of its neighours that are not visited to the queue.
- **Step 4**: Mark all the neighbours as visited.
- **Step 5**: Repeat steps 3 and 4 until the queue is empty.
