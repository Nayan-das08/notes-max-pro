---
subject : DNN
category: 
- lecture-notes
module  : 1
---
#Unlinked 
#incomplete 
2023-01-09

>Links: [[DNN MOC]]

## what is NN
implementation of AI where the hardware mimics the working of brain

## why learn NN
- parallel operation
- learning from envt

werent popular earlier, coz parallel op wasn't available.
now we have powerful and smaller processors

---
## simplest form of NN: perceptron
insert img here

+ve wt -> 
-ve wt -> 

$\theta>= nw-p$
$1, y_{in}>=\theta$
$0$,  otherwise

a decision line is drawn to separate poisitive and negative responses. may also be called decision making line, decision support line.

eg: bipolar step activation function is used over the calculated net input yin, then the value of funciton is one for positive net input and -1 for negative net input.

it is clear that there exists a boundary bw the regions where yin > 0 and yin < 0

can be determined by relation yin = 0

consider a single layer network with 2 inputs, then line is given by 
$$
\begin{align}
b+x_1w_1+x_2w_2=0 \\
x_2=\frac{-b-x_1w_1}{w_2} \\
x_2=\frac{-b}{w_2}-\frac{x_1w_1}{w_2}
\end{align}$$
for positive response, yin > theta, i.e. x_1w_1 + x_2w_2 > theta
then line is x_1w_1 + x_2w_2 = theta

