## MCQ 1: Introduction to Big O Notation

### Q1: **True or False**: If $f(n) = \log n$, then $f(n)$ is $O(n^2)$.

**True.** 
This is not a strict upper bound. When $c = 1$, $c\cdot n^2$ is larger than $\log n$ for all $n \geq 1$. 

### Q2: What is/are the time complexity of `f4`? Select only the tightest bound(s) on the time complexity of `f4`.

**Answers:** Options A and G only. (50 points)
- Option `A` - $O(1)$, if the size of the integers in `arr` is constant.
- Option `G` - $O(n^2)$, where $n$ is the number of bits used for `arr[0]`.

Multiplication is $O(1)$ if the size of the integers is constant. Suppose both integers have a fixed size of 4 bytes (32 bits). Then multiplication of two 32-bit numbers would involve $O(32^2)$ computations, which is $O(1)$ time. 

Multiplication is $O(n^2)$ if we define $n$ to be the number of bits. [It is similar to multiplying two $n$ _digit_ numbers (ie. in base 10).](https://www.basic-mathematics.com/multiplication-in-base-two.html)

Part marks were awarded if you selected more correct than incorrect answers. 

### Q3: What is the time complexity of `f5`?
Select only the tightest bounds on the time complexity of `f5`.

Answer: $O(n^2)$, where $n$ is the input value of $n$.

Let $T(n)$ be the recurrence relation defined by function `f4`.

So $T(n) = T(n-1) + T(\frac{n}{2}) + \theta(1)$

**Intuition for Proof:**

When we write the function calls:

- $T(0)$ is the base case, it has 1 call
- $T(1)$ makes 1 calls to $T(0)$, it has a 2 function calls (increased by 1 from $T(0)$ )
- $T(2) = T(1) + T(1)$, it has a total of 2 + 2 + 1 = 5 calls (increased by 4 from $T(1)$ )
- $T(3) = T(2)$, it has a total of 5 + 1 = 6 calls (increased by 1 from $T(2)$ )
- $T(4) = T(3) + T(2)$, it has a total of 6 + 5 + 1 = 12 calls (increased by 5 from $T(3)$ )
- $T(5) = T(4)$, it has a total of 12 + 1 = 13 calls (increased by 1 from $T(4)$ )
- $T(6) = T(5) + T(3)$, it has a total of 13 + 6 + 1 = 20 calls (increased by 7 from $T(5)$ )

and so on.

We can see that this is **not** a linear growth trend. Hence, we cannot say that it is bounded by $O(n)$, as when $n$ increases, the number of recursive calls incurred from $n$ and $n-1$ increases at a non-linear growth rate. 

$O(2^n)$ is incorrect as the number of recursive calls does not double each time we increase $n$ by 1.

Hence, the logical conclusion is that `f4` is bounded by $O(n^2)$, where $n$ is the input value of $n$.

### Q4: In this case for f6, what could f(n) represent such that it is a good measure of the time complexity?

Option D and E only. 
- Option D - Number of times Line 4 runs
- Option E - Number of times Line 5 runs

It is the only line representative of the time complexity. Time Complexity of the function is $O(NK)$, it is the inner for loop that runs $NK$ times.

Full marks were awarded if:
- You selected option E only
- You selected option D and E only

Part marks were awarded if you selected more correct than incorrect answers. 
