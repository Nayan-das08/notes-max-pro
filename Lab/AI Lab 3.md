---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 3
Jan 12, 2023

## Objective
To perform Depth First Search (DFS) algorithm.

## Theory
Depth-first search (DFS) is a popular algorithm used for traversing or searching a tree or graph data structure. The algorithm starts at a particular node or vertex and explores as far as possible along each branch before backtracking. It is called a depth-first search because it prioritizes exploring the deepest branches of the tree or graph first. DFS can be implemented using either recursion or a stack data structure, and is commonly used in a variety of applications such as maze-solving, path-finding, and cycle detection. 

One of the advantages of DFS is that it requires less memory compared to breadth-first search (BFS), which explores all the neighbouring nodes of a given vertex before moving to the next level. However, it is important to note that DFS may not always find the shortest path or solution, since it only prioritizes exploring the deepest nodes first.

---
## Source Code
```
import networkx as nx
import matplotlib.pyplot as plt
from networkx.drawing.nx_pydot import graphviz_layout

tree = [
    [0 , 1 , 2 , 3 , 4 , 5 , 6 , 7 , 8 , 9 , 10, 11],
    [1 , 0 , 1 , 1 , 1 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
    [2 , 1 , 0 , 0 , 0 , 1 , 1 , 0 , 0 , 0 , 0 , 0 ],
    [3 , 1 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
    [4 , 1 , 0 , 0 , 0 , 0 , 0 , 1 , 1 , 0 , 0 , 0 ],
    [5 , 0 , 1 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
    [6 , 0 , 1 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
    [7 , 0 , 0 , 0 , 1 , 0 , 0 , 0 , 0 , 1 , 0 , 0 ],
    [8 , 0 , 0 , 0 , 1 , 0 , 0 , 0 , 0 , 0 , 0 , 0 ],
    [9 , 0 , 0 , 0 , 0 , 0 , 0 , 1 , 0 , 0 , 1 , 1 ],
    [10, 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 1 , 0 , 0 ],
    [11, 0 , 0 , 0 , 0 , 0 , 0 , 0 , 0 , 1 , 0 , 0 ]    
]

output = []
edge_label = {}
count = 1

def get_neigbours(row, visited):
    nodes = []
    edges = []
    for i in range(1,len(row)):
        if row[i] == 1 and i not in visited:
            nodes.append(i)
            edges.append((row[0], i))
    return nodes,edges

def draw_graph(edges):
    g = nx.Graph()
    g.add_edges_from(edges)
    pos = graphviz_layout(g, prog="dot")
    nx.draw_networkx(
        g,
        pos=pos, 
        edge_color='black', 
        width=1, 
        linewidths=1,
        node_size=500, 
        font_color='w'
    )

    nx.draw_networkx_edge_labels(
        g,
        pos=pos,
        edge_labels=edge_label,
        rotate=False
    )
    plt.show()

def dfs(stack, visited, edge_list, iter=0):
    iter += 1

    print()
    global count
    edge_label[edge_list.pop()] = count
    count += 1

    v = stack.pop()
    print(f'pop {v}')
    n_nodes, n_edges = get_neigbours(tree[v], visited)
    # print(n_edges)

    output.append(v)
    [stack.append(i) for i in n_nodes]
    [visited.append(i) for i in n_nodes]
    [edge_list.append(i) for i in n_edges]

    print(f'connected: {n_nodes}')
    print(f'stack    : {stack}')
    print(f'visited  : {visited}')

    if len(stack) > 0:
        dfs(stack, visited, edge_list, iter=iter)
    else:
        return




# ----------------------------


edges = []
nodes = [i for i in range(1,len(tree))]
for i in range(1,len(tree)):
    for j in range(i,len(tree)):
        if tree[i][j] == 1:
            edges.append((i,j))

stack = [1]
visited = [1]
edge_list = []

print(f'stack    : {stack}')
print(f'visited  : {visited}\n')

v = stack.pop()
print(f'pop {v}')
n_nodes, n_edges = get_neigbours(tree[v], visited)

output.append(v)
[stack.append(i) for i in n_nodes]
[visited.append(i) for i in n_nodes]
[edge_list.append(i) for i in n_edges]

print(f'connected: {n_nodes}')
print(f'stack    : {stack}')
print(f'visited  : {visited}')


dfs(stack, visited, edge_list)
print('\n')
print(f'order of traversal (as per DFS): {output}')

draw_graph(edges)
```

---
## Output
```
stack    : [1]
visited  : [1]

pop 1
connected: [2, 3, 4]
stack    : [2, 3, 4]
visited  : [1, 2, 3, 4]

pop 4
connected: [7, 8]
stack    : [2, 3, 7, 8]
visited  : [1, 2, 3, 4, 7, 8]

pop 8
connected: []
stack    : [2, 3, 7]
visited  : [1, 2, 3, 4, 7, 8]

pop 7
connected: [9]
stack    : [2, 3, 9]
visited  : [1, 2, 3, 4, 7, 8, 9]

pop 9
connected: [10, 11]
stack    : [2, 3, 10, 11]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11]

pop 11
connected: []
stack    : [2, 3, 10]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11]

pop 10
connected: []
stack    : [2, 3]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11]

pop 3
connected: []
stack    : [2]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11]

pop 2
connected: [5, 6]
stack    : [5, 6]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11, 5, 6]

pop 6
connected: []
stack    : [5]
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11, 5, 6]

pop 5
connected: []
stack    : []
visited  : [1, 2, 3, 4, 7, 8, 9, 10, 11, 5, 6]


order of traversal (as per DFS): [1, 4, 8, 7, 9, 11, 10, 3, 2, 6, 5]
```

![[Figure_1.png]]