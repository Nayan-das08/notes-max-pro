- two classes
	- uninformed/blind
		- no info on number of steps from current to goal state
		- eg: bfs, dfs
		- can;t say soln is optimal
		- explores all the alternatives
		- do not have any domain specific knowledge
		- BFS: 
			- expand all nodes level-wise
			- 
		- DFS: 
			- expand nodes and go till the depth before traversing next branch
			- algo
			```
			DFS(C)
				if initial is goal, quit, return success
				else
					generate successor (E) of current state (C), 
					if no successor then signal failure
					call DFS(E)
					if success returned signal success, else loop
			```
		- 
	- informed/heurestic
		- will select the path as per the heurestic value
		- efficient


