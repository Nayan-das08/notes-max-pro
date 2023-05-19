---
subject : AIML
category: notes
---
Dec 18, 2022

>%%Links: [[_AIML MOC]]%%

## definition
establishing relationship between different input variables and the output value to predict the latter value for a new and unknown set of input vector

Consider the data consisting of the size of the houses in an area and their corresponding prices which is given to us before hand.

![[Pasted image 20221218160421.png|500]]

In regression analysis, we need to find a *line*, or more importantly, the **equation of the line** which fits reasonably well on the data and ultimately helps us predict the value of price ($y$) for any value of size ($x$), say 1250 sq. feet. 

![[Pasted image 20221218161128.png|500]]

This is an example of linear regression as the equation of the line is *linear*, i.e. a *straight line*. More importantly, it is **simple** *linear regression* as the output value is considered a function of only **one variable**.

This falls under supervised learning as we **train** the model to accurately predict the value of output (here, price of house) **using examples** of correct values of output for corresponding input values.

## terminologies
for the table of dataset

| **size ($x$)** | **price ($y$)** |
| ---------- | ---------- |
| 2104       | 400        |
| 1416       | 232        |
| 1534       | 315        |
| 852        | 178        |
| ...        | ...        |

| symbol               | meaning                           |
| -------------------- | --------------------------------- |
| $x$                  | **input variable** or **feature** |
| $y$                  | **output variable** or **target** |
| $m$                  | total number of training sample   |
| $(x^{(i)}, y^{(i)})$ | $i^{th}$ training sample          |

---
## Simple Linear Regression
As per the supervised learning technique,
- obtain the training set containing the features and the target
- feed this to the *learning algorithm*
- the algorithm will produce some function, which is known as the **hypothesis function**.
- This hypothesis function is then used to determine the value of target variable for new sets of features
	- for new values of $x$, the functions $f$ will give its best estimate for target variable $\hat{y}$.
	- $x$ is called the *feature*
	- $f$ is called the *model*
	- $\hat{y}$ is called the *prediction*, estimated value of $y$

Since we are only dealing with linear relationship between feature and target right now, so we can express the *hypothesis function* as: $$f_{w,b}(x)=wx+b$$The function takes $x$ as input and gives estimate value of target variable on the basis of coefficients $w$ and $b$.

The value the function gives out is checked against the actual value from training set, and this is done with the help of **[[cost function]]**
