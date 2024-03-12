# Priority Queues

Sometimes, it becomes necessary to suspend everything that is running, and complete the high priority tasks first.

The problem here is that the new tasks can come up dynamically, and we need to process them at the time of execution. 

To solve this problem, we define a new data structure known as **Priority Queue**

## Operations required
The priority queue needs to have two main functions:
- `delete_max()` or `delete_min()` - This function identifies the smallest or largest element and remove it.
- `insert()` - This function adds a new item to the queue based on the priorities.

## Assumption
We will assume that a total of $N$ entries enter and leave the priority queue

## Strategy
### Structure of priority queue
- It is a $\sqrt{N}\text{ x }\sqrt{N}$ array.
- Each row is in sorted order.
- We keep track of `size` of each row

### Strategy for `insert()`
To insert any element in the priority queue, we find the first row that has space, i.e., we find the first row whose `size !=` $\sqrt{N}$ and insert the element such that the row remains in sorted order.

#### Time Complexity
The time complexity of this approach is:
- $O(\sqrt{N})$ time for finding the row with a space
- $O(\sqrt{N})$ time for inserting the element inside the row with free space

So the asymptotic time complexity of this function is $O(\sqrt{N})$

### Strategy for `delete_max()` or `delete_min()`
We have defined the **priority queue** to have all the rows sorted. So we make use of it here, when we want to delete maximum or minimum element.

1. We can take the `maximum` or `minimum` element from each row 
2. Then we find the `maximum` or `minimum` of all those element obtained from step $1$ 
3. Then update the size of the row from where the element is deleted from step $2$

#### Time complexity
The time complexity of this function is:
- $O(1)$ for finding the largest or smallest element in the row
- $O(\sqrt{N})$ for finding the element to be deleted
- $O(1)$ to delete the element

So the asymptotic time complexity of this function is $O(\sqrt{N})$

## Time complexity of the `Priority Queue`
So for the priority queue, 

- Insert function has the time complexity of $O(\sqrt{N})$
- Delete function has the time complexity of $O(\sqrt{N})$

Now assume that we start with an empty **Priority Queue**, then to add and delete $N$ entries, the total time complexity is $O(N\sqrt{N})$