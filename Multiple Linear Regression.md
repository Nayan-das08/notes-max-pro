---
subject : AIML
category: notes
---
Dec 24, 2022

>%%Links: [[_AIML MOC]]%%

We can have multiple features affecting the output variable instead of only one (like in case of Simple Linear Regression). 

For example, for **predicting** the *price of a house*, feature like *size*, *# bedrooms*, *# floors*, *built when*, etc. are the features that may affect the outcome. Thus, it is better to perform Multiple Linear Regression when possible instead of Simple Linear Regression. 

The list of features can also be called a *vector* of input variables or features, denoted by *$x_j$ for $j \le n$ where $n$ is the number of features*.

The vector $X^{(i)}=[x_1^{(i)}, x_2^{(i)}, x_3^{(i)}...x_n^{(i)}]$ can represent the features of $i^{th}$ training sample.

## hypotheses function for Multiple Linear Regression
previously, for one variable/feature, it was 
$$f_{w,b}(x)=wx+b$$
Now it will be
$$\begin{align}
f_{W,b}(X)=(W \cdot X) + b
\end{align}$$
where $W=[w_1, w_2, w_3... w_n]$ is the vector of weights for corresponding features.
The dot represent *dot product* of the two arrays *W* and *X*.

## gradient descent for multiple linear regression
cost function would be 
$$J(W,b)=\frac{1}{2m}\sum^{m}_{i=1}(f_{W,b}(X^{(i)})-{y}^{(i)})^2$$
where the hypothesis function takes an entire vector of input features for $i^{th}$ sample.

For the elements $w_j \in W$ vector, they are updated with the gradient of $W$ $w.r.t$ $w_j$, i.e.;
$$w_j=w_j-\alpha\frac{\partial}{\partial w_j}J(W,b)$$
where
$$\frac{\partial}{\partial w_j}J(W,b)=\frac{1}{m}\sum^{m}_{i=1}(f_{W,b}(X^{(i)})-y^{(i)})x_j^{(i)}$$