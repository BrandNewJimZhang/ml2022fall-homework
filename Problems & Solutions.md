# Problems & Solutions

*Problem 1.* For 2-class problem FLD can be obtained as a special case of MSE. Assume that class $C_1$ has $n_1$ samples $x_1, \cdots, x_{n_1}$ and class $C_2$ has $n_2$ samples $x_j,\cdots,x_{n_2}$. In MSE, we take targets for samples class $C_1$ and $C_2$ to be $b_1=\frac{n}{n_1},b_2=-\frac{n}{n_2}$, respectively. $n$ is the total number of samples, *i.e.* $n=n_1+n_2$. So the sum-of-squares error function can be written as:
$$
E=\frac{1}{2}\sum_{i=1}^n(\boldsymbol{w}^T\boldsymbol{x}_i+w_0-t_i)^2,\qquad
t_i=
\begin{cases}
\displaystyle\frac{n}{n_1}, &\text{if}\,x_i\in C_1 \\
\displaystyle-\frac{n}{n_2}, &\text{if}\,x_i\in C_2 \\
\end{cases}
$$
Our goal is to get the MSE solution of $\boldsymbol{w}$ and $w_0$. Tasks:

1. Prove that the optimal $w_0=-\boldsymbol{w}^T\boldsymbol{m}$, where $\boldsymbol{m}$ is the mean vector of all samples.

2. Derive that the optimal $\boldsymbol{w}$ satisfy the following equation
   $$
   (\boldsymbol{S}_w+\frac{n_1 n_2}{n}\boldsymbol{S}_b)\boldsymbol{w}=n(\boldsymbol{m}_1-\boldsymbol{m}_2),
   $$
   where $\boldsymbol{S}_w$ and $\boldsymbol{S}_b$ are the within-class scatter matrix and between-class scatter matrix, and $\boldsymbol{m}_1, \boldsymbol{m}_2$ are the means of the 2 classes, respectively.

3. Following the equation in (2), derive that $\boldsymbol{w}\propto\boldsymbol{S}_w^{-1}(\boldsymbol{m}_1-\boldsymbol{m}_2)$.

*Solution 1*.

1. $E=1/2\sum_{i=1}^n(w_0+\boldsymbol{w}^T\boldsymbol{x}_i-t_i)^2$,
   $$
   \frac{\partial E}{\partial w_0}=nw_0+\sum_{i=1}^n(\boldsymbol{w}^T\boldsymbol{x}_i-t_i)
   $$
   Let
   $$
   \frac{\partial E}{\partial w^\ast_0}=0,
   $$
   we have
   $$
   \begin{align}
   w_0^\ast&=-\frac{1}{n}\sum_{i=1}^n(\boldsymbol{w}^T\boldsymbol{x}_i-t_i) \\
   &=-\boldsymbol{w}^T\boldsymbol{m}+\frac{1}{n}\sum_{i=1}^nt_i \\
   &=-\boldsymbol{w}^T\boldsymbol{m}.
   \end{align}
   $$

2. We know that $w_0=w_0(\boldsymbol w)$, we have
   $$
   \frac{\partial E}{\partial \boldsymbol{w}}=\sum_{i=1}^n x_i(w^Tx_i-w_0+t_i)
   $$
   after bringing $w_0^\ast=-\boldsymbol{w}^T\boldsymbol{m}$ back to the definition of $E$.
   
   





*Problem 2*. Study the basic formulas of the logistic/sigmoid function.

1. For
   $$
   \theta(s)=\frac{1}{1+e^{-s}},
   $$
   show that
   $$
   \begin{align}
   \theta(s)&=\frac{1}{1+e^{-s}}=\frac{e^s}{e^s+1}, \\
   \theta(-s)&=1-\theta(s), \\
   \theta'(s)&=\theta(s)(1-\theta(s)).
   \end{align}
   $$

2. Study the relationship of the hyperbolic tangent function
   $$
   f(s)=\tanh s
   $$
   with the logistic function $\theta(s)$, and derive the derivative of $f(s)=\tanh s$.

*Solution 2*. 

1. Obviously, we have
   $$
   \theta(s)=\frac{1}{1+e^{-s}}=\frac{e^s}{e^s+1}, \\
   \theta(-s)=\frac{1}{1+e^s}=1-\frac{e^s}{e^s+1}=1-\theta(s),
   $$
   And
   $$
   \theta'(s)=\left(\frac{e^s}{e^s+1}\right)'=\frac{e^s(e^s+1)-e^s\cdot e^s}{(e^s+1)^2}=\frac{e^s}{(e^s+1)^2}=\frac{1}{e^s+1}\cdot\frac{e^s}{e^s+1}=\theta(s)(1-\theta(s)).
   $$

2. We have
   $$
   f(s)=\tanh s=\frac{e^{2s}-1}{e^{2s}+1}=2\theta(2s)-1,
   $$
   And
   $$
   f'(s)=\left(\frac{e^{2s}-1}{e^{2s}+1}\right)'=\frac{2e^{2s}(e^{2s}+1)-2e^{2s}(e^{2s}-1)}{(e^{2s}+1)^2}=\frac{4e^{2s}}{(e^{2 s}+1)^2}=1-\tanh^2(s)=1-(f(s))^2.
   $$