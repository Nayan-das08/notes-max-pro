---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 1B
Jan 5, 2023

## Objective
1.     To create a set
2.     Add members to the set
3.     Remove element from set if element is present

---
## Theory
A set is a collection which is unordered and unindexed. In Python sets are written with curly brackets. To add one item to a set use the add() method.  To add more than one item to a set use the update() method. To remove an item in a set, use the remove(), or the discard() method.

---
## Source Code
```
# Create a set
a = {1,2,3}
print(f'we have set: {a}')

# Add member to the set
# to add one element
print('\na.add(4)')
a.add(4)
print(a)

# to add list of elements
print('\na.update([5,6,7])')
a.update([5,6,7])
print(a)

# Remove element from set
print('\na.remove(1)')
a.remove(1)
print(a)
```

---
## Output
```
we have set: {1, 2, 3}

a.add(4)
{1, 2, 3, 4}

a.update([5,6,7])
{1, 2, 3, 4, 5, 6, 7}

a.remove(1)
{2, 3, 4, 5, 6, 7}
```
