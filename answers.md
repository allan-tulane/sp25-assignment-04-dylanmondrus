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



- **2a.**


- **2b.**


- **2c.**

- **2d.**

- **2e.**



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