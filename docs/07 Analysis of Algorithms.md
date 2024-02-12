# Analysis of Algorithms

We measure the performance of an algorithm in terms of the amount of resources it consumes. The most important resource is time, but other resources such as memory consumption, network usage, storage usage, etc. are also important.

The two main criteria to measure the efficiency of an algorithm are:

- **Running Time**: The amount of time an algorithm takes to complete.
- **Space**: The amount of memory/storage an algorithm uses.

In general, we focus on **time** rather than space, because memory is cheap and abundant, but time is not.

## Measuring Running Time

The **running time** depends on:

### Input Size

**Running time** depends on the size of the input. For example, sorting 10 elements takes less time than sorting 1000 elements in an array.

Measure the running time as a function of the input size, i.e., if the input size is `n`, then the running time is a function of `n`, i.e., `t(n)`.

!!! warning

    Different inputs of the same size `n` may take different amounts of time to execute.

#### Asymptotic Complexity

When comparing `t(n)` focus on the **orders of magnitude** and ignore the constant factors.

We find the **asymptotic complexity** of an algorithm by finding the **order of magnitude** of the running time function `t(n)`.

Mathematically, we find the $lim_{n\to\infin} t(n)$.

Here is a list of most common input sizes and their orders of magnitude based on the `t(n)`:

<figure markdown>
![Input Size complexity](./assets/Input%20Size%20Complexity.png)
<figcaption>Input Size Complexity</figcaption>
</figure>

#### Which Inputs to Consider

Performance of an algorithm can vary across different input instances.

By luck, we can accomplish the task at the start itself or the algorithm may need to run down through the whole input and maybe still not accomplish the task, e.g., finding an element that does not exist in the input.

Hence, we consider the **worst case** where the input forces the algorithm to take longest possible time to complete. By doing this. we may know the **maximum time** that the algorithm requires and hence establish an **upper bound**.

#### Some Points to Note

- Analysis should be independent of the hardware and software environment.
- Don't use actual time.
- Measure the number of operations executed by the algorithm.
