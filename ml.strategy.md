## Bias and variance

High bias: training accuracy lower than baseline.

Solution:
* Bigger network
* Longer training
* Better optimization algorithms
* NN architecture/hyperparameter search

High variance: overfitting, test accuracy << training accuracy

Solution:
* More data
* Regularization
* NN architecture/hyperparameter search

## Techniques
* Orthogonalization
* Single number evaluation metric
* Satisficing and optimizing metric
* Set your dev/test set to be big enough to give high confidence in the overall performance of your system

## Metrics

$$
\begin{aligned}

Precision &= \frac{TP}{TP + FP} \\

Recall &= \frac{TP}{TP + FN} \\

F1\ score &= \frac{2}{\frac{1}{Precision} + \frac{1}{Recall}} \\
&= \frac{2TP}{2TP + FP + FN} \\

\end{aligned} \\
$$
