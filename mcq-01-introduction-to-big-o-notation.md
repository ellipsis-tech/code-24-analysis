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
- $T(1)$ makes two calls to $T(0)$, it has a total of 3 function calls (including the call to itself). (increased by 2 from $T(0)$)
- $T(2) = T(1) + T(1)$, it has a total of 3 + 3 + 1 = 7 calls (increased by 4 from $T(1)$)
- $T(3) = T(2) + T(1)$, it has a total of 7 + 3 + 1 = 11 calls (increased by 4 from $T(2)$)
- $T(4) = T(3) + T(2)$, it has a total of 11 + 7 + 1 = 19 calls (increased by 8 from $T(3)$)
- $T(5) = T(4) + T(2)$, it has a total of 19 + 7 + 1 = 27 calls (increased by 8 from $T(4)$)
- $T(6) = T(5) + T(3)$, it has a total of 27 + 11 + 1 = 39 calls (increased by 12 from $T(5)$)

and so on.

We can see that this is **not** a linear growth trend. Hence, we cannot say that it is bounded by $O(n)$, as when $n$ increases, the number of recursive calls incurred from $n$ and $n-1$ increases at a non-linear growth rate. 

$O(2^n)$ is incorrect as the number of recursive calls does not double each time we increase $n$ by 1.

Hence, the logical conclusion is that `f4` is bounded by $O(n^2)$, where $n$ is the input value of $n$.

For a more formal proof, refer below:

We define a predicate $P(n): T(n) \text { is } O(n^2)$. This means that there exists some constants $c$ and $n_0$ such that $c\cdot n^2$ is bounded by $n$ for all $n\geq n_0$. If $n_0$ is large, we can assume that $n$ is also larger than $n_0$.

Base Cases:
Let $c = 2$ and $n_0 = 2$. Note that for any $n_0 \geq 2$, $2n^2$ is an upper bound for $T(2) \cdots T(6)$.
Hence $P(2) \cdots P(6)$ holds.

Suppose that $P(2) \cdots P(k)$ is true for some $P(k) \geq 2n_0$. Show that $P(k) \implies P(k+1)$.

By the [Strong form of Mathematical Induction](https://math.libretexts.org/Bookshelves/Mathematical_Logic_and_Proof/Gentle_Introduction_to_the_Art_of_Mathematics_(Fields)/05%3A_Proof_Techniques_II_-_Induction/5.04%3A_The_Strong_Form_of_Mathematical_Induction), we can show that 
$$
P(k+1):\\
\implies T(k+1) = T(k) + T(\frac{k+1}{2}) + O(1)\\
\text{Since } P(k) \text { holds and } P(\frac{k+1}{2}) \text { holds, } \\
T(k+1) \leq c\cdot (k-1)^2 + c \cdot (\frac{k}{2})^2 \\
\leq c[k^2 + \frac{k^2}{4} ] \\
= c[\frac{5}{4}k^2] \\
\leq c(k+1)^2 \text { for } k \geq 2n_0
$$
Hence, $P(k+1)$ holds.

The complexity of `f5` is $O(n^2)$.

### Q4: In this case for f6, what could f(n) represent such that it is a good measure of the time complexity?

Option D and E only. It is the only line representative of the time complexity. Time Complexity of the function is $O(NK)$, it is the inner for loop that runs $NK$ times.

Part marks were awarded if you selected more correct than incorrect answers. 
