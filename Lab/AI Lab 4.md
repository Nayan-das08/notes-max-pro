---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 4
Feb 2, 2023

## Objective
To apply $A^*$ algorithm to solve the following 8-puzzle problem configuration:
<center>start state</center>

$$
\begin{array}
{|c|c|c|}
\hline2&8&3\\
\hline1&6&4\\
\hline7&&5\\
\hline
\end{array}
$$
<center>goal state</center>

$$\begin{array}
{|c|c|c|}
\hline1&2&3\\
\hline8&&4\\
\hline7&6&5\\
\hline
\end{array}
$$

## Theory
The 8-puzzle problem is a classic problem in artificial intelligence and computer science that involves a 3x3 grid of numbered tiles with one empty space. The goal is to rearrange the tiles from a scrambled initial state to a desired goal state using only legal moves, which involves sliding one tile into the empty space at a time. The problem is challenging because there are many possible configurations, and some are unsolvable.

This problem is solved using the A* algorithm, which combines heuristic and cost-based search techniques. The algorithm estimates the distance between the current and goal states using a heuristic function and prioritizes nodes with the lowest total cost. The A* algorithm is effective and efficient, although it is not guaranteed to find the optimal solution for every initial state. Various extensions of the A* algorithm have been developed to solve more complex puzzles.

---
## Source Code
```
import copy
import numpy as np
import matplotlib.pyplot as plt

# ------------------

start = [
[2,8,3],
[1,6,4],
[7,0,5]
]

goal = [
[1,2,3],
[8,0,4],
[7,6,5]
]

# ------------------

n = 8+1
m = int(n**0.5)
dir = {0:'up', 1:'down', 2:'left', 3:'right', -1:'null'}

def show_board(board, depth=1):
	space = '    '*depth

	print(f'\n{space}+---+---+---+')
	for i in range(m):
		for j in range(m):
			if j == 0:
				print(space, end='')
			if board[i][j] == 0:
				print(f'|   ', end='')
			else:
				print(f'| {board[i][j]} ', end='')
		print('|')
		print(f'{space}+---+---+---+')

def get_blank_pos(board):
	for i in range(m):
		for j in range(m):
			if board[i][j] == 0:
				return i,j

def swap(board, a,b, c,d):
	temp = board[a][b]
	board[a][b] = board[c][d]
	board[c][d] = temp

def get_opposite_move(move):
	if move == 0:
		return 1
	elif move == 1:
		return 0
	elif move == 2:
		return 3
	elif move == 3:
		return 2
	
def g_displaced_tiles(current, goal):
	count = 0
	for i in range(m):
		for j in range(m):
			if current[i][j] != goal[i][j]:
				# and current[i][j] != 0:
				# print(f'{i},{j} is diff')
				count += 1
	# print(f'no. of tiles displaced: {count}')
	return count

open_list = []
closed_list = []
edges = []
nodes = 0
labels = {} 

def get_label(board):
	# space = '    '*depth
	label = ''
	label += f'\n+---+---+---+\n'
	for i in range(m):
		for j in range(m):
			# if j == 0:
			# 	print(space, end='')
			if board[i][j] == 0:
				label += f'|   '#, end=''
			else:
				label += f'| {board[i][j]} '#, end=''
		label += '|\n'
		label += f'+---+---+---+\n'
	return label

def solve(current, goal, h, prev_move=-1, iteration=1, parent=0):
	print(f'iteration = {iteration}')
	prev_move = get_opposite_move(prev_move)
	h += 1
	space = '    '*h
	# new = copy.deepcopy(current)
	new = []
	# g = []
	# f = []
	for i in range(4):
		new.append(copy.deepcopy(current))
		# g.append(np.inf)
		# f.append(np.inf)
	
	show_board(current)
	r, c = get_blank_pos(current)

	global nodes
	# up
	if r-1 >= 0 and prev_move != 0:
		swap(new[0], r,c, r-1,c)
		g = g_displaced_tiles(new[0], goal)
		f = g+h
		nodes += 1
		temp = {'board':new[0], 'g':g, 'h':h, 'f':f, 'dir_moved':0, 'node_number':nodes}
		open_list.append(temp)
		print('    up')
		edges.append([parent, nodes])
		labels[nodes] = get_label(new[0])

	# down
	if r+1 < m and prev_move != 1:
		swap(new[1], r,c, r+1,c)
		g = g_displaced_tiles(new[1], goal)
		f = g+h
		nodes += 1
		temp = {'board':new[1], 'g':g, 'h':h, 'f':f, 'dir_moved':1, 'node_number':nodes}
		open_list.append(temp)
		print('    down')
		edges.append([parent, nodes])
		labels[nodes] = get_label(new[1])

	# left
	if c-1 >= 0 and prev_move != 2:
		swap(new[2], r,c, r,c-1)
		g = g_displaced_tiles(new[2], goal)
		f = g+h
		nodes += 1
		temp = {'board':new[2], 'g':g, 'h':h, 'f':f, 'dir_moved':2, 'node_number':nodes}
		open_list.append(temp)
		print('    left')
		edges.append([parent, nodes])
		labels[nodes] = get_label(new[2])
		
	# right
	if c+1 < m and prev_move != 3:
		swap(new[3], r,c, r,c+1)
		g = g_displaced_tiles(new[3], goal)
		f = g+h
		nodes += 1
		temp = {'board':new[3], 'g':g, 'h':h, 'f':f, 'dir_moved':3, 'node_number':nodes}
		open_list.append(temp)
		print('    right')
		edges.append([parent, nodes])
		labels[nodes] = get_label(new[3])
	
	f_values = []

	print(f'\nopen list:')
	for i in range(len(open_list)):
		show_board(open_list[i]['board'])
		print(f'    g={open_list[i]["g"]}, h={open_list[i]["h"]}, f={open_list[i]["f"]}')
		f_values.append(open_list[i]["f"])

	
	# among the open list
	min_index = f_values.index(min(f_values))
	chosen = open_list.pop(min_index)
	closed_list.append(chosen)

	print('\nchosen node')
	print(f"g = {chosen['g']}, h = {chosen['h']}, f = {min(f_values)}")
	show_board(chosen['board'])

	print('\n-------------------------------------')	


	if chosen['g'] == 0:
		print(f'\n    GOAL  REACHED')
		# print(f'     in {chosen["h"]:2} steps')
		print(f'     in {iteration:2} steps')
		show_board(chosen['board'])
		return
	else:
		solve(chosen['board'], goal, chosen['h'], prev_move=chosen['dir_moved'], iteration=iteration+1, parent=chosen['node_number'])

g = g_displaced_tiles(start, goal)
h = 0

# show_board(goal,0)
# print("h=0")
labels[0] = get_label(start)
solve(start, goal, h)

import networkx as nx
from networkx.drawing.nx_pydot import graphviz_layout

G = nx.Graph()
G.add_edges_from(edges)
pos = graphviz_layout(G, prog="dot")
nx.draw_networkx(G=G, pos=pos, with_labels = True, node_size=1000)
nx.draw_networkx_labels(G=G, pos=pos, labels=labels, font_size=5, font_family="Consolas",
	bbox=dict(
        facecolor="white",
        edgecolor="white",
        boxstyle="square, pad=0.25",
    )
)
plt.show()
```

---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div>

## Output

<span class="centerImg">![[Figure_3.png|700]]</span>
