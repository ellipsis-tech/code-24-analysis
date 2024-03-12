# Where to Meet for Dinner

#### Description

Code# 2024 Problem

## Problem Statement

A group of $N_l$ friends want to meet at a place for dinner, but they stay in different locations in a Country $X$. Country $X$ has a train transport network such as the one Singapore has.

![Singapore MRT Train Network Map](images/singapore-mrt.jpg)

Let's consider an example using Singapore's train network.

Alice is organizing a dinner with Bella and Clarisse. Alice, Bella and Clarisse live at _Geylang Bahru_, _Woodleigh_ and _Kaki Bukit_ respectively. In order to find a meeting point (or points), we want to ensure that these meeting station(s) minimizes the maximum distance that a single person needs to travel. We call this set of stations $M_{min}$. In the example above, the set of $M_{min}$ stations consists of only _Tai Seng_, as this minimizes the number of stations that a single person needs to travel. 

Every group of $N_l$ friends would also have a combined flexibility score $f$, which indicates the maximum number of stations the group is willing to travel beyond the set of $M_{min}$ stations, only if there are other **more desirable** meeting stations nearby. 

Each station $v$ on the train network is hence also associated with a **popularity score** $P_v$, which could be influenced by the number of malls in the area, for example. Using the example above if _MacPherson_ has a smaller number of malls compared to _Paya Lebar_ and it's only one station away, then it would probably be better to meet at _Paya Lebar_ instead of _MacPherson_. 


We can hence represent this as how **desirable** a particular station is. For a particular person living at station $h$, the **desirability** $D$ of the meeting at station $v$ can be given by:

$$
D(h, v) =  P_v - Dist(h, v)
$$

where $Dist(h,v)$ represents the number of edges along the **shortest path** between $h$ and $v$.

The **most desirable** meeting station (or stations) are those that **maximises** the **minimum desirability** among $N_l$ friends, provided that it is within $f$ stations from the set of $M_{min}$ meeting locations. 

### Question

Given a list of stations $S$ of size $N_s$, a list of station connections $C$ of size $N_c$ each comprising of two station names denoting their connection, a list of popularity scores $P$ of size $N_s$ where $P_i$ represents the favourability score of station $S_i$, a list of locations $L$ of size $N_l$ corresponding to the home locations of the $N_l$ friends, and a flexibility score $f$, find the **most desirable location(s)** to meet for dinner.

If there is more than 1 location, output all of them in a list in the order that they appear in $S$.

If the friends are unable to meet, output the list `["IMPOSSIBLE"]`.

**The train network represented by $S$ and $C$ is undirected and acyclic.**

#### Input Format

The first line contains 2 integers, the value of $N_s$ followed by $N_c$.

The second line contains $S$ space-separated station names, where the $i$-th string represents the station $S[i]$.

The third line contains $S$ space-separated integers, where the $i$-th integer corresponds to the favourability score of station $S[i]$.

The next $N_c$ lines contains 2 station names separated by a space, this indicates that these two stations on that line are adjacent to each other.

The next line contains an integer $T$ denoting $T$ test cases.

For each of the $T$ test cases,

- the first line of each test case contains two space separated integers, corresponding to the number of friends $N_l$, and the flexibility score $f$.
- the next line contains $N_l$ space-separated strings corresponding to list $L$, where the $i$-th string represents $L[i]$, which is the station name where friend $i$ lives.

#### Constraints
- $C$ has a size of $N_c$ rows and $2$ columns
- $S$ is a string of length less than 20 alphanumeric characters. A station name has no whitespaces.
- For each $c = [c_i, c_j] \in C$, let $c_i$ and $c_j$ represent the integers in $c$. 
    - $c_i \neq c_j$
    - Each $[c_i, c_j]$ pair in $C$ is unique.
    - For each $[c_i, c_j]$ pair that exists in $C$, $[c_j, c_i]$ does not exist.
    - Every $c_i, c_j$ contains two station names that are present in $S$
- For each $L_i \in L$,  $L_i$ will represent a valid station in $S$.
- $1 \leq N_c \leq N_s - 1$
- For each $P_i \in P$, $0 \leq P_i \leq 10$
- The graph defined by $S$ and $C$ is acyclic and undirected.
- $1 \leq f \leq 10$

For test cases 1 to 5 (40% of score)
- $1 \leq T \leq 100$
- $1 \leq N_s \leq 50$
- $1 \leq N_l \leq N_s$

For test cases 6 to 10, (60% of score)
- $1 \leq T \leq 10$
- $1 \leq N_s \leq 12^{4}$
- $1 \leq N_l \leq 10**5$

#### Output Format

Output $T$ lines, where each line contains a string or a list of strings separated by a space, representing the most desirable location or locations if possible. Otherwise, that line should output `IMPOSSIBLE`.

#### Sample Input 0

```
15 15
Serangoon Bartley TaiSeng MacPherson PayaLebar Dakota Woodleigh PotongPasir KakiBukit Ubi Mattar GeylangBahru Bendeemeer Eunos Aljunied Kallang
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
Serangoon Bartley
Bartley TaiSeng
TaiSeng MacPherson
MacPherson PayaLebar
PayaLebar Dakota
Kallang Aljunied
Aljunied PayaLebar
PayaLebar Eunos
Bendeemeer GeylangBahru
GeylangBahru Mattar
Mattar MacPherson
MacPherson Ubi
Ubi KakiBukit
PotongPasir Woodleigh
Woodleigh Serangoon
2
3 3
GeylangBahru Woodleigh KakiBukit
2 2
Woodleigh MacPherson
```

#### Sample Output 0

```
TaiSeng
Bartley
```

##### Explanation

The map is similar to the image given in the question, there are 16 stations and 15 connections.

The first sample has all favourability scores set to zero, hence minimizing distance would maximise the minimum desirability among $N$ friends.

There are 2 test cases.

For the first case, meeting at TaiSeng minimises the minimises the maximum distance that everyone needs to travel, hence meeting at TaiSeng is the most desirable.

- Meeting at TaiSeng requires Bella, Alice and Clarisse to move 3 stations. Hence, the desirability of TaiSeng is `-3`.
- Meeting at MacPherson is less desirable. This is because Bella has to move 4 stations, while Alice and Clarisse travel 2 stations. Hence, the desirability of MacPherson is `-4`.

For the second case, meeting at Bartley would be most desirable.

- Meeting at Bartley would 

#### Sample Input 1

```
16 15
Serangoon Bartley TaiSeng MacPherson PayaLebar Dakota Woodleigh PotongPasir KakiBukit Ubi Mattar GeylangBahru Bendeemeer Eunos Aljunied Kallang
1 0 0 0 3 0 0 0 0 0 0 0 0 0 0 0
Serangoon Bartley
Bartley TaiSeng
TaiSeng MacPherson
MacPherson PayaLebar
PayaLebar Dakota
Kallang Aljunied
Aljunied PayaLebar
PayaLebar Eunos
Bendeemeer GeylangBahru
GeylangBahru Mattar
Mattar MacPherson
MacPherson Ubi
Ubi KakiBukit
PotongPasir Woodleigh
Woodleigh Serangoon
2
3 3
GeylangBahru Woodleigh KakiBukit
2 2
Woodleigh MacPherson
```

#### Sample Output 1

```
PayaLebar
Serangoon Bartley
```

##### Explanation

The map is similar to the image given in the question, there are 16 stations and 15 connections.

There are 2 test cases.
In this sample, the favourability scores are no longer all-zeros.

In the first case, the set of $M_{min}$ stations consists of only `TaiSeng`. This group has a flexibility of 3. Since `PayaLebar` has a popularity score of `3`, and it is within 3 stations from `TaiSeng`, then the desirability of `PayaLebar` is -2, which is the highest of all desirabilities in the area.

In the second case, while the minimum desirability of Bartley would be `-2`, `Serangoon` and `PayaLebar` is just as desirable. Serangoon has a popularity score of `1`. This means that the minimum desirability of Serangoon is `-3 + 1 = -2`. PayaLebar is just as desirable too, with a minimum desirability of `-5(max distance to travel) + 3 = -2`. However, PayaLebar is 3 stops away from `Bartley`, which is larger than the group's flexibility score. Hence, `PayaLebar` should not be considered, and the most desirable meeting points include `Serangoon` and `Bartley`. They are displayed in the order shown in the list $S$.
