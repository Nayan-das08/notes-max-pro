>%%Links: [[_AIML MOC]]%%

According to the gradient descent algorithm, the parameter of the model (variables on which cost function depends) should be updated as

$$
\begin{align}
w_i:=w_i-\alpha\frac{\partial J(w_1, w_2...w_n)}{\partial w_i} \\
\end{align}
$$
for any cost function

It is an **optimization algorithm** to obtain the values for which a function (in our case, a cost function) reaches its local minima

From a bow shaped cost function $J(w)$

![[Pasted image 20221218203658.png|300]]

let us be at some value of $w$ that is not the minima. Our intuition for gradient descent algorithm is to move towards the minima, in other words: **in the direction of steepest descent**. 

>[!NOTE]
>- The updating of values $w,b$ must take place *simultaneously*
>- The new values for the parameters must be assigned into the variables at the same time after all the calculations are done

## learning rate $\alpha$
- This determines the speed of movement towards the minima. 
- serves as a *coefficient* on the term being added/subtracted (the gradient)
- **If $\alpha$ is too small**
	- it will take very small increments towards the minima
	- will take a long time to reach the end
- **If $\alpha$ is too large**
	- it will take large increments towards the minima
	- will end up overshooting the minima and keep bouncing between the bow shaped function

## gradient $\frac{\partial J(w_1, w_2...w_n)}{\partial w_i}$
- represents the direction of the steepest descent.
- **positive gradient** 
	- the value of parameter is ahead of the minima
	- we end up subtracting from the actual value
- **negative gradient** 
	- the value of parameter is behind of the minima
	- we end up adding from the actual value
- **zero gradient** 
	- the value of parameter is at the minima
	- the actual value remains unchanged

## gradient descent for [[simple linear regression]]

^61f76d

| function            | math                                                        |
| ------------------- | ----------------------------------------------------------- |
| hypothesis function | $f_{w,b}(x)=wx+b$                                           |
| cost function       | $J(w,b)=\frac{1}{2m}\sum^{m}_{i=1}(f(x^{(i)})-{y}^{(i)})^2$ |

now 
$$
\begin{align}
&\frac{\partial}{\partial w}J(w,b)=\frac{1}{m}\sum^{m}_{i=1}(f_{w,b}(x^{(i)})-{y}^{(i)})x^{(i)}\\
&\frac{\partial}{\partial b}J(w,b)=\frac{1}{m}\sum^{m}_{i=1}(f_{w,b}(x^{(i)})-{y}^{(i)})
\end{align}
$$
## types of gradient descent
1. **Batch Gradient Descent**
	- calculate the gradient using the mean over the cost function of all the samples
	- includes the inputs from all the samples
	- time consuming as it has to add the cost values iteratively

2. **Stochastic Gradient Descent**
	- calculate the gradient from one of the randomly chosen sample and use it to update the parameters
	- does not include the input from all the samples, thus takes time to reach minima
	- very fast compared to previous method

3. **Mini-Batch Gradient Descent**
	- calculate gradient from a batch/subset of randomly selected samples of pre-determined size
	- strikes a balance between including input from the most samples and having an efficient algorithm

