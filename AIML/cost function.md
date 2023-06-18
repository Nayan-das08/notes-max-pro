>%%Links: [[_AIML MOC]]%%

## need?
Key step in building a supervised learning model is to define a cost function

Suppose for a simple linear regression problem, we have a input features and target variables and the model described by 
$$f(x)=wx+b$$
$$w,b: parameters$$
parameters/coefficients/weights are the the variables that can be adjusted during training of the model to obtain required output.

The values of $w$ and $b$ influence the line described by the *hypothesis function*. Here, $w$ is the the slope of the line and $b$ is the y-intercept.

The predicted value $\hat{y}^{(i)}$ is obtained from the value of the *hypothesis function* at $x^{(i)}$, i.e.:
$$\hat{y}^{(i)}=f(x^{(i)})=wx^{(i)}+b$$
We need to find such values of $w,b$ such that the value of $\hat{y}^{(i)}$ is close to $y^{(i)}$$\forall(x^{(i)},y^{(i)})$.

## definition of cost function
it denotes the numerical "cost" the model owes due to the magnitude of the error from the actual value of target variable.

It can be expressed in many ways. Most popular is Squared Sum of Errors (SSE). 

SSE is expressed as:

$$J(w,b)=\frac{1}{2m}\sum^{m}_{i=1}(\hat{y}^{(i)}-{y}^{(i)})^2$$ ^512f55

Here,  ^c05793

| symbol                        | meaning                                                                                      |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| $J(w,b)$                      | cost function is a **function of the weights** of the model                                  |
| $(\hat{y}^{(i)}-{y}^{(i)})^2$ | error between predicted value and actual value, squared to make it absolute                  |
| summation                     | to find the sum of all the errors, so that the final cost includes error from all the points |
| $1/2m$                        | to cancel out the term received after taking the derivative ([[gradient descent]])               |

The term $\hat{y}^{(i)}$ can be expanded and the cost function can ultimately be expressed as 
$$J(w,b)=\frac{1}{2m}\sum^{m}_{i=1}(f(x^{(i)})-{y}^{(i)})^2$$
$$J(w,b)=\frac{1}{2m}\sum^{m}_{i=1}(wx^{(i)}+b-{y}^{(i)})^2$$
### Our ultimate goal is
for model: $f(x)=wx+b$
parameters: $w,b$
cost function: $J(w,b)=\frac{1}{2m}\sum^{m}_{i=1}(f(x^{(i)})-{y}^{(i)})^2$
**goal**: $minimize_{(w,b)} J(w,b)$ 

## example
for dataset

| $x$   | $y$   |
| --- | --- |
| 1   | 1   |
| 2   | 2   |
| 3   | 3   |

we have the distribution as 

![[Pasted image 20221218194641.png|250]]

Now, considering a simpler cost function $f_w(x)=wx$, for $w=1$, we get the cost function $J(w)=0$ 

![[Pasted image 20221218200733.png|250]]

similarly, for $w=0.5$, we get cost function $J(0.5)=0.583$

![[Pasted image 20221218201251.png|250]]

similarly, for $w=1.5$, we get cost function $J(1.5)=0.583$

![[Pasted image 20221218201412.png|250]]

for 20 values of $w$ ranging from 0.25 to 1.75, the values of $J(w)$ is given by

![[Pasted image 20221218203658.png|250]]

We require the value of $w$ for which we can get the lowest value of $J(w)$, and from the last graph, that point is at $w=1$.

In other words, the cost function $J(w)$ has to be minimised

>[!NOTE]
>- for cost function as a function of $w,b$, its graph will be 2-dimensional
>- to visualize the lowest point of the 2D cost function curve, we use **contour maps** of the function, where the value of the function is shown as its projection on $w,b$ plane.

---
There are two common ways to get the appropriate values of the parameters such that the cost function is the lowest possible value (for regression problem):
- Least Square Method
- [[Gradient Descent]]
