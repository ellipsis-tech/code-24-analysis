# Don't Dig Down

#### Description
Singapore Management University Code# 2024 Problem 

## Problem Statement
You are an experienced player in the hit game "TerraCraft". It is a game where you explore mines and caves, grabbing as much loot and ores before extracting back and creating armor and weapons to fight the various bosses that the game has to offer.

You are an Experienced player looking to speedrun the game. After researching the various ways to get the fastest time, you decided to optimize the mining phase the game by breaking the "cardinal" rule of the game: Don't Dig Down.

In paper, digging down the mine seems like a straightforward and simple strategy. That is true until the mine itself detected that you have been digging straight down for too much and proceed to give you debuffs and ambush you with over-leveled enemies.

With your countless hours of the game, you found a method that lets you get around the penalties of the system. Turns out, the penalties only kick in only if it is caused by the player actions themselves, environmental/mobs activities do not count. With this, you decide to collect a large amount of low-level mobs called "Stompers" which can destroy a 1x1 area right underneath them. With a number of these creatures set in a collumn, you can dig straight down without triggering the penalties. 

Unfortunately, if the Stompers destroy an area containing a loot, the loot themselves will be destroyed, so you only are able to grab loot from the right/left side of the holes that the Stompers made.

Combined with your sonar detector, which can detect the total amount of loot `(M)` as well as the location `(X[i]Y[i])` and quality `(A[i])` of each loot in a `N`*`N` mapping of the mine, what is the maximum total quality of loot you can gain?

#### Input Format
The first line contains integer  `N` and `M`, the size of the sonar map and amount of loot respectively <br>
The Second line contains an array `X` of size `M`, containing the X-coordinate location of the `i-th loot`. <br>
The third line contains an array `Y` of size `M`,, containing the Y-coordinate location of the `i-th loot`. <br>
The fourth line contains an array `Q` of size `M`, containing the quality of the `i=th loot`.

#### Constraints:

- $2 \leq$  `N`  $\leq 100,000$ 
- $1 \leq$  `M`  $\leq 200,000$ 
- No area contains more than 1 loot. In other words, X[i]Y[i] ≠ X[j]Y[j] (for each i and j such that 0 ≤ i < j ≤ M − 1).
- $1 \leq$  `Q[i]`  $\leq 10^8$ for each i-th loot



#### Output Format
Output a single line containing integer `Z`, the maximum quality of loot that you can get

#### Sample Input  1
```
3 5
0 2 1 1 2   
2 2 1 0 1
2 3 3 7 2
```
#### Sample Output 1
```
13
```
##### Explanation
- Pic coming soon

#### Sample Input 2
```
5 4
0 1 4 3
2 1 4 3
5 2 1 3
```
#### Sample Output 2
```
11
```

##### Explanation
- The longest subsequence shared between `X` and `Y` is `"CHT"` which has the length of 3. Hence we get 45 Kiloliters

