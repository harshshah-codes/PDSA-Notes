# Why Efficiency Matters

Our code needs to be efficient because in real world we need to work on a huge pile of data and our code needs to be efficient to save our resources and time.

### Real World Example

A mobile network company needs to check whether each of their sim cards are linked to valid Aadhar card. Let us say, there are `N` sim cards and `M` Aadhar Cards.

One of the naive approaches is:

```linenums="1" title="Naive Approach"
foreach simcard S:
    foreach Aadhar_number A:
        check if AadharDetails of S matches A
```

Complexity of this approach = $M.N$

---

#### Problem with the naive approach

Now let us consider the case of India:
There are almost $10^9$ Aadhar cards and $10^9$ Sim cards.

Now the complexity will be $10^{18}$.

As we know python can do $10^7$ operations in `1 sec`.

This operation will therefore take $\frac{10^{18}}{10^7} = 10^{11}\text{secs}$ $\approx 3200\text{ years}$.

To not get into this trap of nested loops, we need our code to be efficient which can be achieved by approaching the problem in another way.

#### Efficient Approach

Assuming, Aadhar numbers list is sorted, one of the way is to use `Binary Search` to search for the aadhar number.

By halving the search for aadhar numbers even 10 times, reduces the time by $2^{10} = 1024$ times.

After 10 queries, the aadhar card space shrinks to $10^6$.

After 20 queries, the aadhar card space shrinks to $10^3$.

After 30 queries, the aadhar card space shrinks to $1$.

Therefore, time taken by the program = $10^9 * 30 \approx 50 \text{ minutes}$.

!!! tip

    Hence, "Efficiency matters."
