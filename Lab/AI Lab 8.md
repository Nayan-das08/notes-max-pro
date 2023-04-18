---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 8
Mar 16, 2023

## Objective
To implement graph colouring using:
1.     Backtracking
2.     Greedy

## Theory
Graph colouring problem is a constraint satisfaction problem in which the vertices of the graph are to be coloured with minimum number of unique colours (chromatic number) such that no 2 adjacent vertices are of the same colour.

---
## Source Code
```
for i in nodes:
    #find the neighbours of the node
    neighbours[i] = list(G.neighbors(i))
    #find the colours of the neighbours
    neighbours_colours[i] = []
    for j in neighbours[i]:
        if j in node_colours:
            neighbours_colours[i].append(node_colours[j])
    #find the colours of the neighbours
    for k in colours:
        if colours[k] not in neighbours_colours[i]:
            node_colours[i] = colours[k]
            break
    #check if the graph is coloured
    for i in nodes:
        if i not in node_colours:
            backtrack()
            break
```

---
## Output
```
GRAPH COLORING PROBLEM
Using Backtracking

Number of nodes : 9

Enter the matrix :
    0  1  2  3  4  5  6  7  8  9
    1  0  1  1  0  0  1  0  0  0
    2  1  0  0  1  1  0  0  0  0
    3  1  0  0  1  0  0  0  0  0
    4  0  1  1  0  0  0  0  1  0
    5  0  1  0  0  0  1  0  1  0
    6  1  0  0  0  1  0  1  0  1
    7  0  0  0  0  0  1  0  1  1
    8  0  0  0  1  1  0  1  0  0
    9  0  0  0  0  0  1  1  0  0

edges: [[1, 2], [1, 3], [1, 6], [2, 4], [2, 5], [3, 4], [4, 8], [5, 6], [5, 8], [6, 7], [6, 9], [7, 8], [7, 9]]

nodes: [1, 2, 3, 4, 5, 6, 7, 8, 9]


With 3 colors, 132 solutions are possible
```

<span class="centerImg">![[Pasted image 20230413101206.png]]</span>
