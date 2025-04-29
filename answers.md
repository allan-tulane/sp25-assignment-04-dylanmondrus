# CMPS 2200 Assignment 5
## Answers

**Name:** Dylan Mondrus





- **1a.**

In a binary heap the maximum depth is log2 n. Therefore in a d-ary heap the maximum depth is logd n. 

- **1b.**
The work for insert is O(logd n) since you swap the depth of the tree in the worst case. 

For delete, you have to compare the root with d children at every level, which is depth log d n. Therefore you multiply the number of comparisons with the number of levels which is thus O(d logd n). 


- **1c.**
In Dijkstra's, you perform one delete-min for each vertex, so |V| operations. You also perform one insert for each edge so |E| insert operations. Delete-min in a d-ary heap costs O(d logd |V|) each, and insert costs O(log d|V|) each. So delete-min is O(|V|dlogd|V|) and insert is O(|E|logd|V|) therefore the total work is O(logd|V| * (|V|d + |E|)).

- **1d.**
A value of d = |V|^epsilon will yield an overall running time of O(|E|).



- **2a.**
APSP(0, 0, 2) = 0
APSP(0, 1, 2) = -2
APSP(0, 2, 2) = -1
APSP(1, 0, 2) = infinity(no path)
APSP(1, 1, 2) = 0
APSP(1, 2, 2) = 1
APSP(2, 0, 2) = infinity(no path)
APSP(2, 1, 2) = infinity(no path)
APSP(2, 2, 2) = 0

- **2b.**
Yes there is a relationship between APSP(i, j, 1) and APSP(i, j, 2). APSP(i,j,2) = min(APSP(i, j, 1), APSP(i, 2, 1) + APSP(2, j, 1)). 
You can write APSP(i, j, 2) in terms of APSPS(i,j,0) and APSP(i,j,1) as APSP(i,j,2) = min(APSP(i,j,1), APSP(i,2,1) + APSP(2,j,1)). 

- **2c.**
APSP(i,j,k) = min(APSP(i,j,k-1), APSP(i,k,k-1) + APSP(k,j,k-1))

- **2d.**
For each parameter in the function, n choices. There are three parameters. Therefore the number of distinct subproblems is n^3 where n is the number of choices made at each subproblem. The amount of work at each subproblem is O(1), so the total work is n^3 * O(1) so the total work is O(n^3). 

- **2e.**
Our dynamic programming algorithm has work O(|V|^3), where V is the number of vertices, and has this work no matter what. 
Johnson's algorithm does O(|V||E| + |V|^2 log|V|) work where V is the number of vertices and E is the number of edges. It is faster when the graph is sparse. Therefore dynamic programming is preferable when the graph is dense with many edges or small with a small number of vertices. 


- **3a.**
Yes, the solution to the minimum spanning tree is guaranteed to be a solution to the minimum maximum spanning tree. This is because MST algorithms always prefer lighter edges first. They never add a heavy edge unless they have no choice. As a result, the heaviest edge in the MST is as small as possible. Thus minimizes the largest edge weight among all possible spanning trees. 


- **3b.**
How do we find the spanning tree with the next lowest total weight after the MST? The second-best MST differs from the best MST by swapping a single edge. 
Algorithm:
1. Start with the MST.
2. For each edge e in the MST:
    - temporarilty remove edge e from the MST.
    - this splits the tree into two components
    - find the smallest-weight edge f that connects these two components, but f =/ e. 
    - form a new tree T' by replacing e with f
    - compute the total weight of T'
3. Among all such candidate trees, pick the one with the smallest total weight
4. Return that tree as the second-best MST
This will give the next-best tree after the MST.


- **3c.**
There are E edges and V vertices. You have scan every edge for V vertices. Therefore the work is O(|V||E|). 