fundamentals about software testing
what is ST, why, what should we test, who should test

## Verification and Validation
- process of evaluation a system or a component of software to determine whether the products of a given development phase satisfy the conditions imposed at the start of that phase.

we check whether it satisfies the specified requirements

$\text{Testing = Verification + Validation}$ 

## Alpha, Beta and Acceptance testing
### acceptance
- when software is developed for a specific customer
- done by the end users/customer themselves
- may range from ad hoc tests to well planned systemic series of tests

below are when software is developed as a product for anonymous customers
### Alpha
- conducted at developer's side
	- by some potential customers
	- or by those who has used or has idea about similar software
- conducted in controlled envt.

### Beta
- conducted by end users / customers at their sides
- developer is not present
- conducted in a real envt.
- developer has no control

## levels of testing
### 1. unit testing
- each module is tested separately

### 2. integration testing
- modules that are to be connected for their operation (coupling) tested together to check their interconnection and dependency

### 3. system testing
- all the modules (as per requirement) are connected, the complete system is ready, entire system is tested as a whole


## Black Box Testing
- we will check only for functionality
- by checking inputs and corresponding outputs
- not concerned with structure
- some testing methods under Black Box Testing

### Boundary Value Analysis (BVA)
- concerns with boundary values of inputs
- minimizes the test cases
- not effective to test only the boundary values
- instead of only two, take $min+1$, $middle$ and $max+1$ values as well
- $\text{input = \{min, min+, norm, max-, max\}}$ 

![[IMG20230329101002 1.jpg]]

how to determine total number of test cases
>Ans: $4n+1$
>$n$ is number of inputs

how testing is shown / performed

| test id case | input    | expected output |
| ------------ | -------- | --------------- |
| 1            | $a_1$, $b_1$ | $o_1$                |
| 2            |          |                 |
| 3            |          |                 |

>[!HW]
>find limitations of BVA method
>ans: *Boolean inputs*

limitations: 
- no invalid test cases are taken
	- solution: **Robustness Testing**
	- $\text{input = \{min-, min, min+, norm, max-, max, max+\}}$ 
	- no of test cases: $6n+1$

**Worst Case Testing**
cartesian product of ?

> question 1
>Consider a program for the determination of nature of roots of a quadratic equation. Input is a triple positive integer: a, b, c and values are from interval $[0,100]$, program output may have one of the following words: not quad, real roots, imaginary roots, equal roots

design the boundary value test cases

| test case | a   | b   | c   | expected output |
| --------- | --- | --- | --- | --------------- |
| 1         | 0   | 50  | 50  | not quad        |
| 2         | 1   | 50  | 50  | real roots      |
| ...       |     |     |     |                 |
| 13        |     |     |     |                 |

- no of test cases = $4(3)+1$ = 13
- distribution of test values for **a**: $\{0,1,50,99,100\}$
- keep values of **b** and **c** as middle value
- change only one variable at a time, keep others constant

>question 2
>consider a program for determining the previous date. Its input is a triple of day, month, year with the values in the range
>- $1 \le month \le 12$
>- $1 \le day \le 31$
>- $1900 \le year \le 2025$
>outputs: valid date, invalid date

distribution of test values

| input | values                         |
| ----- | ------------------------------ |
| month | $\{1,2,6,11,12\}$              |
| day   | $\{1,2,15,30,31\}$             |
| year  | $\{1900,1901,1962,2024,2025\}$ |

| test case | month | day | year | expected outcome |
| --------- | ----- | --- | ---- | ---------------- |
| 1         | 1     | 15  | 1962 | valid            |
| 2         | 2     | 15  | 1962 | valid            |
| 3         | 6     | 15  | 1962 | valid            |
| 4         | 11    | 15  | 1962 | valid            |
| 5         | 12    | 15  | 1962 | valid            |
| 6         | 6     | 1   | 1962 |                  |
| 7         | 6     | 2   | 1962 |                  |
| 8         | 6     | 30  | 1962 |                  |
| 9         | 6     | 31  | 1962 |                  |
| 10        | 6     | 15  | 1900 |                  |
| 11        | 6     | 15  | 1901 |                  |
| 12        | 6     | 15  | 2024 |                  |
| 13        | 6     | 15  | 2025 |                  |


### Equivalence Class Partition (ECP)
- input domain of the program is divided into finite no of equivalence classes
- equivalence classes are identified by taking each input condition and dividing it into valid and invalid classes.
	- eg: for a from 0 to 50, 40 is valid, but less than 0 and greater than 50 is invalid
	- valid: $[0 \le a \le 50]$ 
	- invalid: $[a < 0]$ and $[a > 50]$ 
- no test cases = no of classes
- redundancy
	- when using nominal value, redundant cases will arise
	- won't arrive when use value other than nominal 
- advantage: 
	- less no of test cases

### Decision Table Based Testing (DTBT)


### Cost Effect Graphing Testing (CEGT)

## white Box Testing
- we will check the structure of the software
- also known as structural 