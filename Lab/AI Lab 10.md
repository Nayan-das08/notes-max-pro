---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 10
Mar 30, 2023

## Objective
To implement 0/1 Knapsack using Brute Force approach

## Theory
A set of objects with different weights and their values is given. The objective of 0/1 knapsack problem is to find the most optimal subset of these objects such that the total weight of these objects should not exceed a certain amount and the summation of values of these objects should be the maximum possible value incurred.

Brute Force approach is a method in which all 2^n combinations of the objects are taken 1 by 1 and the combination satisfying the above constraints is selected. E.g., if the objects with weights and values are given as follows and the maximum capacity is 40.

| item | weight | value |
| ---- | ------ | ----- |
| 0    | 30     | 10    |
| 1    | 10     | 20    |
| 2    | 40     | 30    |
| 3    | 20     | 40    |

---
## Source Code
```
def knapsack_brute_force(values, weights, capacity):
    n = len(values)
    max_value = 0
    best_subset = None
    # Generate all possible subsets of items
    for i in range(2**n):
        subset = []
        subset_weight = 0
        subset_value = 0
        for j in range(n):
            if (i >> j) & 1==1:
                subset.append(j)
                subset_weight += weights[j]
                subset_value += values[j]
        # Check if the subset is feasible and has higher value than previous best
        if subset_weight <= capacity and subset_value > max_value:
            max_value = subset_value
            best_subset = subset
    return max_value, best_subset
knapsack_brute_force([10,20,30,40],[30,10,40,20],40)
```

---
## Output
```
(60, [1, 3])
```