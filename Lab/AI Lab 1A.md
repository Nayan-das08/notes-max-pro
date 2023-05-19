>%%Links: [[Lab Files]]%%

# Experiment 1A
Jan 5, 2023

## Objective
To implement AND, OR and XOR gates and design the truth tables for the same.

---
## Theory

| Gate     | equation | condition                                  |
| -------- | -------- | ------------------------------------------ |
| AND Gate | A & B    | 1 if both of them are 1, else give 0       |
| OR Gate  | A \| B   | 1 if any of them are 1, else give 0        |
| XOR Gate | A ⊕ B    | 1 if both of them are unequal, else give 0 | 

### AND Gate
![[Pasted image 20230105123433.png]]

| A   | B   | A & B |
| --- | --- |:-----:|
| 0   | 0   |   0   |
| 0   | 1   |   0   |
| 1   | 0   |   0   |
| 1   | 1   |   1   |

### OR Gate
![[Pasted image 20230105123511.png]]

| A   | B   | A \| B |
| --- | --- |:------:|
| 0   | 0   |   0    |
| 0   | 1   |   1    |
| 1   | 0   |   1    |
| 1   | 1   |   1    |

### XOR Gate
![[Pasted image 20230105123523.png]]

| A   | B   | A ⊕ B |
| --- | --- |:-----:|
| 0   | 0   |   0   |
| 0   | 1   |   1   |
| 1   | 0   |   1   |
| 1   | 1   |   1   |

---
## Source Code
```
def AND(a,b):
    if a == 1 and a == 1:
        return 1
    else:
        return 0

def OR(a,b):
    if a == 1 or b == 1:
        return 1
    else:
        return 0

def XOR(a,b):
    if a != b:
        return 1
    else:
        return 0

a = [0,0,1,1]
b = [0,1,0,1]

print('A\tB\tA&B\tA|B\tA⊕B')
for i in range(len(a)):
    #c.append(AND(a[i],b[i]))
    print(f'{a[i]}\t{b[i]}\t {AND(a[i],b[i])}\t {OR(a[i],b[i])}\t {XOR(a[i],b[i])}')

print('\n')

x = int(input('Enter X : '))
y = int(input('Enter Y : '))

print()
print(f'{x}&{y} = {AND(x,y)}')
print(f'{x}|{y} = {OR(x,y)}')
print(f'{x}⊕{y} = {XOR(x,y)}')
```

---
## Output
```
A       B       A&B     A|B     A⊕B
0       0        0       0       0
0       1        0       1       1
1       0        1       1       1
1       1        1       1       0


Enter X : 1
Enter Y : 1

1&1 = 1
1|1 = 1
1⊕1 = 0
```
