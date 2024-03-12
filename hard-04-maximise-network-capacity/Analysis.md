# Analysis
Our goal is to create a $D$ partition on frequency ranges $R$ such that the size of each partition is as small as possible.

It is obvious that the strategy of dividing the boards into $k$ partitions won't work for all cases. 

### Way 1: By Dynamic Programming
We can implement a solution using recursion with the following optimal substructure property:
- Assuming we already have $D-2$ partitions in place, we now have to put the $D-1$-th divider to get $D$ partitions. 
- We can put the $D-1$-th divider between the $i$-th and $i+1$ element where $i = 1\cdots |R|$.
- The total cost of this arrangement can be calculated as the **maximum** of the following:
1. The cost of the last partition: $\sum_{i=1}^n R[i]_{max} - R[i]_{min}$. 
2. The maximum cost of any partition already formed to the left of the $k-1$-th divider. We can observe that this is actually to place the $k-2$ separators to place the $k-2$ separators as fairly as possible (so this is a subproblem of the given problem).

Thus, we can write the optimal substructure property as the following recurrence:
$$T(D, N) = \min\{ \max_{i\in{[1,D]}}{T(i, N-1), \sum_{j=i+1}^n R[j]_{max} - R[j]_{min}} \}$$

with base cases
$T(1,k) = R[0]$ and $T(n,1) = \sum_{i=1}^n R[i]_{max}-R[i]_{min}$

With Dynamic Programming, this solution would take $O(DN^3)$ time and $O(D N)$ auxillary space.

### Way 2: Using Binary Search

The idea is to apply Binary Search Approach.
The invariant of Binary Search to the Painter's Problem is based on the following observations:
- the target value would always be in the searching range
- the searching range will decrease in each loop so that the termination can be reached
- We also know that the values in this range must be in sorted order.

Here our target value is the value of $B_{max}$.

By fixing the possible low to high for the target value and narrow down our search to get the optimal allocation. 
- We can see that the **highest possible value in this range is the sum of all elements** in the array and this happens when we have 1 device that has the whole network to itself.

- The lowest possible value of this range is the **maximum bandwidth value** of a range, as in this allocation. Note that it is not possible for $B_{max}$ to be smaller than this.

- If we take the number of devices to be an arbitrary variable $x$, when the target value $B_{max}$ increases, $x$ decreases and vice-versa.

Hence, we can re-frame the problem to find the target value when $x = D$ using binary search.

This is the optimal solution to the problem, with a time complexity of $O(D\log{\sum_{i=1}^n R[i]_{max} - R[i]_{min}})$ time, and $O(1)$ auxillary space.


