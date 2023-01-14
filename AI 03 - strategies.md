## classes of production system
1. **monotonic**
	1. when two rules are applied simultaneously
	2. one rule doesn't affect the other
	3. can co-exist
2. **non monotonic**
	1. increases problem solving efficiency
	2. eliminates prev records
	3. does not allow backtracking
	4. used for solving ignorable problems
3. **partially commutative**
	1. when 2 or more rules used to derive a result
	2. combination of the same rules produces the same result
4. **commutative**
	1. for problems in which changes can reverse the outcome
	2. sequence of operation is not critical


## control strategies
which rule has to be applied next while searching for the soln of a problem witin problem space, w/o getting stuck at any point

requirements
- control stategy should cause motion
- control stategy should be systematic


## search strategies
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
	- informed/heurestic
		- will select the path as per the heurestic value
		- efficient

## informed search techniques
reduce the amount tof search/traversal using some heurestic function

fn that ranks alt in various search algo at each branching step based on the available info

hill climbing
- discrete optimization algo
- DFS+h value
- simple and steepest ascent hill climbing/gradient search
- drawback: local maxima, plateau, ridge
- how to overcome: backtracking

best first search
- combination of DSF and BFS and h value
- maintains 2 lists: open and closed lists

a*
- $f(n)=g(n)+h(n)$ 
- $g(n)$ -> sum of edge costs from start to node n
- $h(n)$ -> estimate of lowest cost path from node n to goal
- algo
- 

i want kitkat
ao*
constraint satisfaction

