# Slime Hero

#### Description
Singapore Management University Code# 2024 Problem 

## Problem Statement
In the Land of Alliance, there once was a hero named Gale.

Despite hailing from the slime race, do not let his looks deceive you. His body might seem frail and weak, yet his wits and bravery led him clearing out numerous dungeons across the land.

One day, Gale heard of a dungeon called the "Rogue Web". A dungeon made deep down in a ravine by the ancient race of arachnids shaped akin to those of spider webs. The architecture of the dungeon also transforms periodically so noone really knows for sure its structure nor its content.

Seeking intel, Gale went to the nearby tavern and found you, an expert Seer who has the power to gather information that no others could. 

With your power, you determined that there are `N` rooms in the dungeon that can be visualised as a connected graph with `N` vertices and `N-1` edges. 

You also scouted the amount of enemies in each room, being `A`$_i$ for the `i`-th room. Due to the location of the dungeon, Gale can start from any room by jumping down the ravine. Looking for challenge, gale is determined to challenge rooms with strictly more enemies than the room directly right before.

Thanks to his slime-y origins, Gale also has the power to split himself as many times as he wants without compromising his power, allowing him to tackle multiple rooms at once. 

Once all rooms are cleared or there are no more room that satisfies the requirements, Gale will be teleported out of the dungeon.

Help Gale determine the highest amount of room that he can clear and how many enemies he defeated along the way. 

In case of two(2) or more path that yield the same maximum amount of rooms cleared, choose the one with the more enemies defeated.

#### Input Format
The first line contains an integer `N`, denoting the number of rooms.
The second line contains `N` integers. The i-th integer is `A`$_i$, the number of enemies of room i. The next `N-1` lines each contain two integers `X`$_i$ and `Y`$_i$ that shows that room `X`$_i$ and `Y`$_i$ are directly connected

#### Constraints:

- $1 \leq$ `N`$\leq 10^{6}$ 
- $1 \leq$ `A`$_i\leq 10^{4}$ for all `i`
- $0 \leq$ `X`$_i$, `Y`$_i\leq N$ for all `i`

#### Output Format
For each test cases, output a line containing `X Y` where `X` is the maximum amount of rooms cleared, and `Y` is the number of enemies defeated

#### Sample Input  1
```
5
1 2 3 4 3
1 3
2 3
4 3
4 5
```
#### Sample Output 1
```
3 9
```
##### Explanation
- To be added with pics 

#### Sample Input 2
```
8
10 5 9 5 3 1 8 8
3 7
3 5
2 6
2 5
8 7
1 2
4 2
```

#### Sample Output 2
```
4 27
```

##### Explanation
- To be added with pics 




