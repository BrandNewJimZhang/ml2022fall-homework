# Solution of Computer Exercise 4

This is the solution of computer exercise 4. In this exercise, I developed a very simple neural network to predict the mortality of ICU patients. 

## model

The model is a very simple neural network with 2 hidden layers.

### layers

1. input layer: 1 neuron for each feature. 108 neurons are needed because we have 108 features.
2. hidden layer 1: 50 neurons
3. hidden layer 2: 20 neurons
4. output layer: 1 neuron

### activation, loss function and iteration algorithm

1. activation function: sigmoid function for every layer except the output layer
2. loss function: $E=\frac{1}{2}(y-d)^2$
3. iteration algorithm: gradient descent
   for each iteration, we update the weights of each layer by

   $$
   \boldsymbol{w}^{(t+1)}=\boldsymbol{w}^{(t)}-\eta\frac{\partial E}{\partial \boldsymbol{w}^{(t)}}
   $$

   where $\eta$ is the learning rate.

### accuracy

Because there is only one output neuron, we can use the following formula to calculate the accuracy:

$$
\text{accuracy}=\frac{1}{N}\sum_{i=1}^N\left\{\begin{array}{ll}
1, & \text{if }y_i\geq 0.5\text{ and }d_i=1, \\
1, & \text{if }y_i<0.5\text{ and }d_i=0, \\
0, & \text{otherwise}.
\end{array}\right.
$$

## code

Just run `homework.ipynb` in the folder.

### basic report

I did a 5-fold cross validation on the training set. The accuracy is 

| fold | 1     | 2     | 3     | 4     | 5     |
| ---- | ----- | ----- | ----- | ----- | ----- |
| acc  | 0.535 | 0.772 | 0.774 | 0.766 | 0.756 |

And I trained another model of the whole training set and tested it on the test set. The accuracy is 0.526.

### changing learning rate

I changed the learning rate from 0.5 to 0.0005 (0.5, 0.2, 0.1, 0.05, 0.02, 0.01, 0.005).