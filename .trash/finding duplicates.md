#compcode

for finding duplicates in an array, there are several methods

## sort
- method
	- sort the array
	- find the repeating element
- time complexity: $O(nlogn) + O(n)$
- this modifies the array

## set
- method
	- traverse the array
	- put each element in a set
	- if an element already exists in a set, it is the duplicate
- time complexity: $O(n)$
- not in constant space

binary tree problems
leetcode cookbook
the art of computer programming