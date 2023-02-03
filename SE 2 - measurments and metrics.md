## measurement
- fundamental to any engineering discipline
- we require some mechanism to measure
- software metrics
	- broad range of measurements for software
	- enables a dev to measure diff aspects of a software
- software process
	- measurement can be aplied to improve it on a continuous basis
- software project
	- controling the activities involved in a project
- measurements used by engg in decision making

## terms
1. measure
2. measurement
	- act of determining measure
3. metric
	- quantitative measure
4. indicator

## why measure
- to indicate the quality of product
- to assess the productivity of ppl working on the production
- to assess the benifit derived from new method or tool
- to form baseline for estimation (cost or schedule)
- to help justify requests for new tools or training

## types of software measurements
- direct measure
	- easy to collect
	- eg:
		- cost
		- effort
		- line of code
		- speed
		- memory size
		- errors
- indirect measure
	- diff to assess
	- eg:
		- quality
		- functionality
		- complexity
		- reliability

## types of metrics
### process metrics
- measures such as overall dev time, type of methodology used
- collected across *all projects* over *long period of time*
- to provie *indicators* that lead to *long-term software process* imporovement
	- to obtain estimations for software dev process

### product metrics
- 
2. project metrics

## factors affecting software quality
1. product
2. people
3. technology
4. process

## example
- 2 team, 2 diff projects
- they recording errors in a software process
- team a finds 342 
- team b finds 184
- *which team is more effective*: 
	- we can't say without having any knowledge about the softwares
	- two softwares projects are independent of each other (as of know)
	- we need normalization for this

## normalization of metrics
- 2 ways
	- size oriented metrics
	- function oriented metrics

## Size oriented Metrics
- while calc LOC
	- dont include header files
	- dont include comment and blank lines
- with LOC
	- errors per KLOC
	- $ (productivity) per KLOC
	- pages of doc per LOC
	- errors per person-month
	- LOC per person-month

## albrecht's func oriented metrics
- 5 *functional* components/*point*
	1. input 346
	2. output
	3. enquiries
	4. internal logical files
	5. external interface files
- no adjustments can be made to these functional points
- weighting factors are used as per the usage/requirements
- UAF = Unadjusted Functional Point
- CAF = Complexity Adjustment Factor
- formulae
	- $FP=UFP \times CAF$
	- $UFP=\sum^{5}_{i=1}\sum^{3}_{j=1}z_{ij}w_{ij}$ 
	- $CAF=0.65+(0.01 \times \sum f_i)$
- Altho not procatically impossible, but if $CAF=0$, $FP=UFP$ 
- FP can be used to evaluate
	- productivity
		- FP/person-month(effort)
	- quality
		- defect/FP
	- cost
		- rupees/FP
	- documentation
		- pages of doc/FP
		- DOCOMO model

| functional units | low | avg | high |
| ---------------- | --- | --- | ---- |
| inputs           | 3   | 4   | 6    |
| outputs          | 4   | 5   | 7    |
| inquiries        | 3   | 4   | 6    |
| logical files    | 7   | 10  | 15   |
| interface files  | 5   | 7   | 10   |

0 - no influence
1 - incidental
2 - moderate
3 - average
4 - significant
5 - essential


CAF
1. does the system require reliable backup and recovery
2. is data comm required
3. are there distribute processing functions
4. is performance critical
5. will the system run in an existing heavily utilized operational evnt

---
consider project
- input - 50
- output - 40
- inquiries - 35
- files - 06
- interface - 04

assume all complexity adjusment factors and weighing factors as average. Compute function points for the project

UFP = 50x4 + 40x5 + 35x4 + 6x10 + 4x7 = 628
CAF = 0.65 + (0.01x14x3) = 1.07
FP = 672

---
input 10 low
output 12 high
inquiries 12 avg
files 20 low
interface 15 high
CAF 1.10

what are the unadjusted and adjusted func point counts

UFP = 10x3 + 12x7 + 12x4 + 20x7 + 15x10
CAF = 1.10

---
project
- inputs
	- 10 low = 30
	- 15 avg = 60
	- 17 high = 102
- output
	- 6 low = 24
	- 13 high = 91
- inquiries
	- 3 low = 9
	- 4 avg = 16
	- 2 high = 12
- files
	- 2 avg = 20
	- 1 high = 15
- interface
	- 9 low = 45

requires
- significant data comm = 4
- poerfomance critical = 5
- code may be moderately reusable = 2
- sys not designed for multiple installation in diff org = 0
other adj factors are avg

compute FP

UFP = 424
CAF = 0.65 + (0.01(4+5+2+0+30)) = 1.06
FP = 449.44

---

## token count
- *token*: operands and the operators used in the software/program
- we can find
	- **the size of vocabulary of the program, $n$**
		- $n=n_1+n_2$
		- $n_1$: no of unique operators
		- $n_2$: no of unique operands
	- **length of program, $N$**
		- $N=N_1+N_2$
		- $N_1$: total occurrences of operators
		- $N_1$: total occurrences of operands
	- **volume, $V$**
		- $V=Nlog_2n$
		- base 2 chosen for *bits*
	- **potential volume, $V^*$**
		- $V^*=(2+n_2^*)log(2+n_2^*)$
		- $n_2^*=roundoff(log_2(n_2), 0)$ 
	- **program level, $L$**
		- $L=V^*/V$
		- value will be 0 to 1
		- $L=1$: program written in highest possible level
	- **program difficulty, $D$**
		- $D=1/L=D \times V$ 
	- **effort, $E$**
		- $E=V/L$
	- **estimated program length**
		- $N=n_1logn_1+n_2logn_2$

