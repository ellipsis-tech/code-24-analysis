# Analysis

### Way 1: Brute Force Solution
We need to make two observations for this to work:

1. Given our metric for desirability, it doesn't matter if multiple friends stay at a particular location. Hence, the number of friends we are meeting is independent of its complexity.

2. The maximum distance a person has to travel is given by the last node we encounter in our BFS traversal from any meeting point.

Since all edges have the same weight, we can do a BFS to get the shortest path from the source vertex to a destination vertex. 

Each BFS iteration requires $O(N_s)$ time, since $N_c\leq N_s-1$ for an acyclic directed graph.

We can find the set of $M_{min}$ stations by treating every vertex as the meeting point, and do a BFS from each vertex. If we encounter a vertex that is one of the friends, and if we find that they are in different connected components, we output `IMPOSSIBLE`.

After finding this set of $M_{min}$ stations, we do a BFS from the set of $M_{min}$ stations as the source vertices, with at most $f$ levels of the tree.

From the set of reachable stations, we can select the most desirable meeting points.

This algorithm takes $\Theta(N_s^2)$ time, since we cannot escape having to traverse the whole set of $N$ vertices.


### Way 2: Greedy Breadth First Search
This other algorithm offers some optimization through pruning the tree. We also take advantage of two more properties:

3. The sum of distances that the whole group of $N$ friends needs to travel is **constant**.
4. For an acyclic graph, for every step we take outside the $M_{min}$ stations, the maximum distance will always increase by 1.

We can use property 3 to **prune our BFS tree**. We first select the home of one friend, and consider their adjacencies. Here there are three cases:
- Case 1: Neighbour has a larger max distance --> because the graph is acyclic, it is not possible that any $M_{min}$ station lies on this path.
- Case 2: Neighbour has a smaller than or equal max distance --> we only take steps toward a node with smaller than or equal maximum distance.

After we reach a point where all children are larger, we have arrived the set of $M_{min}$ stations and can also return the `maxDist` at the $M_{min}$ stations.


Now, we can find the distances of only those nodes in the region of $f$ by leveraging property 4:
- Since we have the smallest `maxDistance` that corresponds to the set of $M_{min}$ stations, if a node is not in the set of $M_{min}$, the maximum distance is 1 larger than the max distance of the previous station.

Hence, we are able to find the stations within the boundary of $f$ from $M_{min}$ stations at the same time as finding the reachable stations nearby.

This algorithm takes $O(N_s^2)$ time, but due to the optimizations, $O(N_s^2)$ time is a large upper bound. 







