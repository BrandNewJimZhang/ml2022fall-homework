# Solutions of Computer Exercise 3

## Usage of `sklearn.neighbors.KneighborsClassifier()`

Lorem ipsum

## The choice of $k$ in $k$-NN algorithm (odd numbers only)

```python
clf = KNeighborsClassifier(n_neighbors=k)
```

For different $k$ in `n_neighbors` in this problem, the accuracy score for training set and test set can be plotted as below:

![](selecting-k.png)

This plot can bring us several ideas:

* When $k=0$, training accuracy is 1. (obviously)
* With the increase of $k$, training accuracy decreases and test accuracy increases and converges (not mathematically) to a certain value.

Let's set $k=5, 25, 51, 151$ and observe for training set and test set:

![](output.png)

With the increase of $k$, the area of training accuracy decreases and area of test accuracy increases. But there is no need to set $k$ too large, because the area of test accuracy will not increase too much. In this problem, $k=25$ is a good choice.

