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

limitations: 
- no invalid test cases are taken
	- solution: **Robustness Testing**
	- $\text{input = \{min-, min, min+, norm, max-, max, max+\}}$ 

**Worst Case Testing**
cartesian product of ?

### Equivalence Class Partition (ECP)
### Decision Tree Based Testing (DTBT)
### Cost Effect Graphing Testing (CEGT)

## white Box Testing
- we will check the structure of the software