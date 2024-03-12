# Park Pathways

#### Description

Code# 2024 Problem

## Problem Statement

In Gardens By The Bay, there are `N` points of interest connected by `M` pathways. Each pathway connects two different points and can be traversed in both directions. The park is designed in such a way that there is at most one direct pathway between any two points.

Your task is to write a program that determines whether it's possible to visit all points of interest by starting at any point and traversing each pathway exactly once. Your program should output a boolean value (`True` or `False`).

#### Input Format

- The first line contains an integer, `Q`, representing the number of test cases.
- For each test case, the first line contains an integer `N`, representing the number of points of interest and second line contains integer `M`, representing the number of pathways.
- The next `M` lines describe the pathways. Each line contains two integers `a` and `b`, indicating there is a pathway between points `a` and `b`.

#### Constraints:

- $1 \leq$ `Q` $\leq 10,000$
- $1 \leq$ `N` $\leq 25$
- (`N` - 1) $\leq$ `M` $\leq$ (`N` \* (`N` - 1)) / 2
- $1 \leq$ `a`, `b` $\leq$ `N`

#### Output Format

- Return `True` if it's possible to visit all points by traversing each pathway exactly once.
- Otherwise, return `False`.
- Take note that Hackkerank will call your function `Q` times and convert your outputs to `1` and `0` respectively, each printed on a new line.

#### Sample Input 0

```
1
4
3
1 2
2 3
3 4
```

#### Sample Output 0

```
1
```

### Sample explanation 0

![](https://code-sharp-images.s3.amazonaws.com/easy-03-park-pathway/positive+test.png)
Since it is possible to visit all POI's through by traversing each path once, this is a positive test case.

#### Sample Input 1

```
1
5
4
5 3
3 4
1 5
2 3
```

#### Sample Output 1

```
0
```

#### Sample explanation 1

![](https://code-sharp-images.s3.amazonaws.com/easy-03-park-pathway/negative+test.png)
In this case, it is impossible to navigate through all POI's without backtracking. If you would like visit POI 2, you would have to go from POI 3 and to POI 2 and return back to POI 3 (backtracking), hence traversing the same path more than once.
