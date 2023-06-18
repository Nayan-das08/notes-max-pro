>%%Links: [[_AIML MOC]]%%

## what is it?
Refers to the algorithms that learn by learning **how to map vector of inputs $X$ to output label $y$.**

The algorithms receives/learns from **correct examples** of problem conditions and the corresponding solution.

The process is analogous to how a child learns about different things as its parents teach it with correct examples. For example, by analysing the features of a dog, we can easily identify the animal as a dog because we were trained how a dog looks like.

## popular applications
- spam filtering (emails), 
- speech recognition, 
- language translation, 
- online advertising
- self driving car
- visual inspection in factories

## types of algorithms
The supervised algorithms can be classified into two groups:

### Regression
It can be described as prediction of output quantity for some new input value

It works to establish a **relationship between the input vector $X$ and the output value $y$**. We refer to the output as a *value* as the output in case of regression is quantitative data. For qualitative data, we use Classification

Some common examples are:
- predicting house pricing on the basis of various characteristics that one might deem important for this analysis
- understanding relationship between advertising and profit/sales
- studying relationship between drug dosage and various parameter changes in the body
- etc.

There are different types of regression for different needs
- **Linear Regression** ^5450a3
	- the relationship is limited to degree 1, i.e. linear
	- [[Simple Linear Regression]]
	- [[Multiple Linear Regression]]
- **Polynomial/Curvilinear Regression** ^376c22
	- the degree of relationship can be any integer

Other types of regression (found from [net](https://www.statology.org/types-of-regression/))
- Ridge Regression
- Quantile Regression
- Poisson Regression
- Lasso Regression

### Classification
can be described as mapping/establishing relationship between input vector and an **output class/label**

This output value is a **quantitative data** and thus differs from Regression

Some common examples are:
- various **ailment detection** by studying the reports and forming relationships between various parameters and the probability of the report being positive for the concerned illness
- **spam filtering** in emails where the algorithm studies the parameters of emails like content, sender, address, frequency and thus determines if the email is spam or not
- **monitoring social media** pages and to determine if a certain account is following the community guidelines or not

Classification can be **binary**, or **multi-class**

---
[[cost function]] plays an **important role in ALL** supervised learning algorithms


