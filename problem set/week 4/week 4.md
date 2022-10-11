# Problem & Solution

**I fix some typo in the original problem set in this solution file.**

*Problem.* For a 3-layered MLP model (with 1 hidden layer): The MLP model is for multi-class classification. The hidden nodes all use the ReLU activation function
$$
f(net_j)=\max(0, net_j),
$$

and the output nodes use the softmax activation function

$$
y_j=\frac{e^{\boldsymbol{w}_j^T\boldsymbol{O}_h}}{\sum_{k=1}^K e^{\boldsymbol{w}_k^T\boldsymbol{O}_h}},\quad j=1,\ldots,K,
$$

where $K$ is the number of classes, $\boldsymbol{O}_h$ is the output of the hidden layer, and $\boldsymbol{w}_j$ is the weight vector of the $j$-th output node. 

Derive the weight-updating formula of the BP algorithm for this MLP.

*Solution.*

Let's derive the softmax function. The softmax function is defined as

$$
f(\boldsymbol{x})=\left(\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\right)_n,\quad \boldsymbol{x}=(x_1,\ldots,x_n)\in\mathbb{R}^n.
$$

The derivative of the softmax function is

(1) If $i=j$,

$$
\begin{align}
\frac{\partial f_i}{\partial x_j}&=\frac{\partial}{\partial x_j}\left(\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\right) \\
&=\frac{e^{x_i}\sum_{j=1}^n e^{x_j}-e^{x_i}e^{x_j}}{\left(\sum_{j=1}^n e^{x_j}\right)^2} \\
&=\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\left(1-\frac{e^{x_j}}{\sum_{j=1}^n e^{x_j}}\right) \\
&=\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\left(1-f_j\right) \\
&=f_i\left(1-f_j\right).
\end{align}
$$

(2) If $i\neq j$,

$$
\begin{align}
\frac{\partial f_i}{\partial x_j}&=\frac{\partial}{\partial x_j}\left(\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\right) \\
&=\frac{-e^{x_i}e^{x_j}}{\left(\sum_{j=1}^n e^{x_j}\right)^2} \\
&=-\frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}\frac{e^{x_j}}{\sum_{j=1}^n e^{x_j}} \\
&=-f_if_j.
\end{align}
$$

So the derivative of the softmax function is given as,

$$
\frac{\partial f_i}{\partial x_j}=\begin{cases}
f_i\left(1-f_j\right), & i=j, \\
-f_if_j, & i\neq j.
\end{cases}
$$

or using Kronecker delta $\delta_{ij}=\begin{cases}1,\quad i=j \\ 0, \quad i\neq j\end{cases},$

$$
\frac{\partial f_i}{\partial x_j}=f_i(\delta_{ij}-f_j).
$$

Because the loss function is defined as

$$
L=\frac{1}{2}\sum_{j=1}^K\left(y_j-d_j\right)^2,
$$

where $d_j$ is the desired output of the $j$-th output node, the derivative of the loss function is

$$
\frac{\partial L}{\partial y_j}=y_j-d_j.
$$

For layer $l$, the weight updating formula should be

$$
\boldsymbol{w}_l\leftarrow\boldsymbol{w}_l-\eta\frac{\partial L}{\partial\boldsymbol{w}_l}= \boldsymbol{w}_l-\eta\boldsymbol{\delta}_l\boldsymbol{x}_{l-1}^T,
$$

where for the output layer

$$
\boldsymbol{\delta}_l=\frac{\partial L}{\partial\boldsymbol{O}_l}f'(\boldsymbol{net}_l)=(\boldsymbol{y}-\boldsymbol{d})^T \boldsymbol{f}'(\boldsymbol{net}_l)
$$

where $\boldsymbol{f}'(\boldsymbol{net}_l)$ is 

$$
\boldsymbol{f}'(\boldsymbol{net}_l)=(f_i(\delta_{ij}-f_j))_{i\times j},\quad \delta_{ij}=\begin{cases}1,\quad i=j, \\ 0, \quad i\neq j,\end{cases}
$$

and for the hidden layer

$$
\boldsymbol{\delta}_l=\frac{\partial L}{\partial\boldsymbol{O}_l}\boldsymbol{f}'(\boldsymbol{net}_l)=\boldsymbol{w}_{l+1}^T\boldsymbol{\delta}_{l+1}\boldsymbol{f}'(\boldsymbol{net}_l),
$$

where $\boldsymbol{f}'(\boldsymbol{net}_l)$ is

$$
\boldsymbol{f}'(\boldsymbol{net}_l)=(\varphi(net_{ij})),\quad\varphi(x)=
\begin{cases}
1, &x>0, \\
0, &x<0.
\end{cases}
$$

