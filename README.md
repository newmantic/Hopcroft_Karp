# Hopcroft_Karp


The Hopcroft-Karp algorithm is an efficient method for finding the maximum matching in a bipartite graph. Let's break down the explanation step by step, including all relevant mathematical symbols.


A bipartite graph G = (U, V, E) is a graph where the vertex set V can be divided into two disjoint sets U and V such that every edge (u, v) in E connects a vertex u in U to a vertex v in V.

A matching M in G is a set of edges such that no two edges share a common vertex. The size of a matching is the number of edges in it. A maximum matching is a matching that contains the largest possible number of edges.

An augmenting path is a path that starts and ends at unmatched vertices, with edges that alternate between edges not in the matching and edges in the matching.

If an augmenting path is found, the matching can be increased in size by "flipping" the edges along the path. Specifically, the edges that were not in the matching are added, and the edges that were in the matching are removed.


The Hopcroft-Karp algorithm alternates between two main phases: the BFS (Breadth-First Search) phase and the DFS (Depth-First Search) phase. The algorithm works in iterative rounds until no more augmenting paths can be found.

1. BFS Phase
The algorithm first performs a BFS to find the shortest augmenting paths from unmatched vertices on the left side U.
During BFS, the algorithm constructs a level graph where each vertex is assigned a level based on the shortest distance from the unmatched vertices.
The BFS ensures that only the shortest augmenting paths are considered in the DFS phase.

2. DFS Phase
After BFS, the algorithm performs DFS from the unmatched vertices on the left side U to find augmenting paths using the level graph constructed during BFS.
The DFS attempts to extend the current matching by finding augmenting paths and updating the matching accordingly.
If a new augmenting path is found, the matching size is incremented.

3. Repetition and Termination
The BFS and DFS phases are repeated iteratively until no more augmenting paths can be found.

The algorithm terminates when the BFS phase fails to find any augmenting path, indicating that the current matching is a maximum matching.


Initialization:
Let M = {} (initially, the matching is empty).
Let dist[u] be the distance from u to the nearest unmatched vertex (initialized to infinity).

BFS Phase:
For each u in U where u is unmatched, set dist[u] = 0 and enqueue u.
For each vertex u in U in the queue:
For each edge (u, v) in E, where v is a vertex in V:
If v is unmatched, set dist[u] = dist[u] + 1 and enqueue the pair-mate of v.

DFS Phase:
For each u in U where u is unmatched, perform DFS to find augmenting paths.
If a path is found, update M by adding edges not in M and removing edges in M.

Termination:
Repeat the BFS and DFS phases until the BFS phase fails to find any augmenting paths.
The size of M is then the size of the maximum matching.


The Hopcroft-Karp algorithm runs in O(E * sqrt(V)) time, where E is the number of edges and V is the number of vertices in the graph. This makes it highly efficient for large bipartite graphs.

