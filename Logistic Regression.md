Classification algorithm used for binary class problems. 

The sigmoid function is used in logistic regression to model the probability. 
$$\sigma(x)=\frac{1}{1+e^{-x}}$$
We incorporate this sigmoid function in the linear regression model to obtain the logistic regression model. 

Let $z(x)=wx+b$. Put this value and take its sigmoid. We will get
$$\begin{align}
\sigma(z(x))&=\frac{1}{1+e^{-z}} \\
&=\frac{1}{1+e^{-(wx+b)}}
\end{align}$$
Thus, with the sigmoid function you can get the probability at $x$ and with parameters $w$ and $b$ you can manipulate the obtained probability/prediction to reduce the loss.
$$\therefore f_{W,b}(X)=\sigma(W \cdot X+b)$$

after manipulation of $f(X)$, we get
$$\frac{f(X)}{1-f(X)}=e^{W \cdot X + b}$$
where the LHS is called *odds* (having value from $0$ to $\infty$). The log of odds is called *logit* and is given by
$$ln\left(\frac{f(X)}{1-f(X)}\right)=W \cdot X + b$$
which gives us the decision boundary