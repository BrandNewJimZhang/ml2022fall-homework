# Solutions of Problem Set 3

## Question 1

Search on the Internet and in the literatures to find popular methods/criteria used for assessing and comparing performances of multi-class classifiers. Write a short summary on the topic with your discussion on the properties of the methods.

### Measurement of Performance

Choosing the right (or best) metric to measure the performance of a classifier is important. The metric should be able to capture the performance of the classifier in a way that is meaningful to the problem at hand. One should notice that considerations such as the cost of misclassification, the number of classes, and the type of data (e.g. continuous or discrete) should be taken into account when choosing a metric. There is no single metric that is best for all problems. The following are some of the most popular metrics used for evaluating the performance of classifiers:

#### Classification Summary or Report[^1]

The classification summary or report is a table that summarizes the performance of a classifier. It contains the number of true positives, false positives, true negatives, and false negatives. But for a multi-class classifier, the table will be trimmed as a table showing the performance of each class. The table can be used to calculate the accuracy, precision, recall, and F1 score of the classifier. The accuracy is the ratio of the number of correct predictions to the total number of predictions. The precision is the ratio of the number of true positives to the total number of true positives and false positives. The recall is the ratio of the number of true positives to the total number of true positives and false negatives. The F1 score is the harmonic mean of the precision and recall. The harmonic mean is the reciprocal of the arithmetic mean of the reciprocals of the precision and recall. 

#### Confusion Matrix[^2]

A confusion matrix shows the combination of the actual and predicted classes. The rows of the matrix represent the actual classes while the columns represent the predicted classes. The diagonal of the matrix shows the number of correct predictions while the off-diagonal shows the number of incorrect predictions.

#### Cohen’s $\kappa$[^3]

Cohen’s $\kappa$ Statistic measures the proximity of the predicted classes to the actual classes when compared to a random classification.

#### Cross-Entropy[^4]

Cross-entropy is a measure of the difference between two probability distributions. It is used to measure the performance of a classifier. The lower the cross-entropy, the better the performance of the classifier.

[^1]: https://medium.com/apprentice-journal/evaluating-multi-class-classifiers-12b2946e755b
[^2]: Fawcett, Tom (2006). "An Introduction to ROC Analysis". *Pattern Recognition Letters*. **27** (8): 861–874.
[^3]: McHugh, Mary L. (2012). "Interrater reliability: The kappa statistic". *Biochemia Medica*. **22** (3): 276–282.
[^4]: The Mathematics of Information Coding, Extraction and Distribution, by George Cybenko, Dianne P. O'Leary, Jorma Rissanen, 1999, *p. 82*.

## Question 2

It is straightforward to apply the nearest neighbor method (1-NN) on multi-class classification
tasks. If we want to use k-nearest neighbor (k-NN) method for multi-class classification, how
should we choose k and what problems we may meet? For example, how a decision should be
made if there is a tie in the voting? Study the possible questions by yourself or look for
literatures, and write a short essay on it.

### Choosing $k$

Choosing the value of $k$ is important. If $k$ is too small, the classifier will be sensitive to noise. If $k$ is too large, the classifier will be insensitive to the local structure of the data. The value of $k$ should be chosen such that the classifier is neither too sensitive nor too insensitive to the data. Overall, it is recommended to have an odd number for k to avoid ties in classification, and cross-validation tactics can help you choose the optimal k for your dataset.

### Disadvantages of $k$-NN

The disadvantages of $k$-NN include the following:

- Does not scale well: Since KNN is a lazy algorithm, it takes up more memory and data storage compared to other classifiers. This can be costly from both a time and money perspective. 

- Curse of dimensionality: The KNN algorithm tends to fall victim to the curse of dimensionality, which means that it doesn’t perform well with high-dimensional data inputs. 

- Prone to overfitting: Due to the “curse of dimensionality”, KNN is also more prone to overfitting. While feature selection and dimensionality reduction techniques are leveraged to prevent this from occurring, the value of k can also impact the model’s behavior. Lower values of k can overfit the data, whereas higher values of k tend to “smooth out” the prediction values since it is averaging the values over a greater area, or neighborhood. However, if the value of k is too high, then it can underfit the data. 
