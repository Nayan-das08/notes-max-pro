---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 7
Mar 9, 2023

## Objective
To create a program to solve Cryptarithmetic Problems.

## Theory
Cryptarithmetic problems are mathematical puzzles in which the digits are replaced by letters of the alphabets. The goal is to decipher the alphabet by using standard arithmetic rules.

```
  SEND
+ MORE
------
 MONEY
```

The most common type of cryptarithmetic problem is where the digits are replaced by letters of the English alphabet. In these problems, each letter represents a unique digit. The goal is to find the digits that make the equation true.

There are several techniques that can be used to solve cryptarithmetic problems. One of the most common techniques is to use a brute-force approach, where all possible combinations of digits are tried until a solution is found. Another technique is to use a heuristic approach, where certain rules are followed to narrow down the possible solutions.

---
## Source Code
```
import itertools
def get_value(word, substitution):
    s = 0
    factor = 1
    for letter in reversed(word):
        s += factor * substitution[letter]
        factor *= 10
    return s

def solve2(equation):
    # split equation in left and right
    left, right = equation.lower().replace(' ', '').split('=')
    # split words in left part
    left = left.split('+')
    # create list of used letters
    letters = set(right)
    for word in left:
        for letter in word:
            letters.add(letter)
    letters = list(letters)
    digits = range(10)
    for perm in itertools.permutations(digits, len(letters)):
        sol = dict(zip(letters, perm))
        if sum(get_value(word, sol) for word in left) == get_value(right, sol):
            print(' + '.join(str(get_value(word, sol)) for word in left) + " = {} (mapping: {})".format(get_value(right, sol), sol))
solve2('APPLE+LEMON=BANANA')
```

---
## Output
```
67794 + 94832 = 162626 (mapping: {'p': 7, 'a': 6, 'b': 1, 'm': 8, 'n': 2, 'o': 3, 'e': 4, 'l': 9})
```