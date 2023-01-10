---
subject : 
category: 
- lecture-notes
module  : 
---
#Unlinked 
#incomplete 
2023-01-06

>Links: [[AI MOC]] 

process of generating soln from observed data

key elements
- state
- state space
- operators
- initial state
- goal/final state

how to solve
define the problem
analyze the problem
isolate and represent the known data
choose the best technique

characterisitics of a problem
- is problem decomposable
	- can be broken down into sub-problems
	- such can be solved easily
- steps undone or ignored
	- in theorem proving, a lemma that has been proved can be ignored for next steps
	- recoverable/backtracking
	- eg: 8-puzzle (recoverable), chess (not)
	- recoverable can be solved using backtracking
	- irrecoverable solved by recoverable style using *planning*
- universe prictable
	- we know what will happen on each move (8-puzzle)
	- in chess/bridge anything can happen 
	- planning used here to guarantee a soln
	- seq of operators to have a good prob of leading to a good soln
- good soln absolute or relative
	- absolute is the only soln
		- multiple paths can be taken to reach goal state
	- relative is when we have a no of soln, and we choose the best
		- eg: TSP
- solution a path or a goal
	- finding a consistent interpretation
- role of knowledge
	- playing chess
		- knowledge is impm only to constrain the search for a soln
	- reading newspaper
		- 
- requires human interaction
	- solitary problem
	- conversational problem

## State space rep
- set of all possible states for a given problem
- operators required to move from initial state to goal state
- can;t visualize the state space always, limited resources
- eg: coffee preparation, 8-puzzle problem


>[!HW]
>make state space tree for the 8-puzzle (from ppt)

## Water Jug Problem
given
- 4 gallon and 3 gallon jug
- pump of unlimited of water

start state

goal state
- need 2 gallon in 4 gallon jug

operators

rules

soln
2
9
2
7
5
11/9

>[!HW]
>- implement in python
>- draw state space soln of missionary-cannibal problem

## 8-puzzle

## missionary-cannibal problem

## n queens

