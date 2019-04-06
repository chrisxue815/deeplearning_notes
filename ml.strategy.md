## Basic recipe

Orthogonalization: implement controls that only affect a single component of your algorithm's performance at a time.

High bias: training accuracy lower than baseline. Solution:
* Bigger network
* Longer training
* Better optimization algorithms
* NN architecture/hyperparameter search

High variance: overfitting, test accuracy << training accuracy. Solution:
* More data
* Regularization
* NN architecture/hyperparameter search

## Setting up your goal

* Single number evaluation metric
* Satisficing and optimizing metric
* Choose a dev set and test set to reflect data you expect to get in the future and consider important to do well on
* Set your dev/test set to be big enough to give high confidence in the overall performance of your system

### Metrics

$$
\begin{aligned}

Precision &= \frac{TP}{TP + FP} \\

Recall &= \frac{TP}{TP + FN} \\

F1\ score &= \frac{2}{\frac{1}{Precision} + \frac{1}{Recall}} \\
&= \frac{2TP}{2TP + FP + FN} \\

\end{aligned} \\
$$

## Human-level performance

Bayes error rate: the lowest possible error rate for any classifier of a random outcome.

Use human-level error as a proxy/estimate for Bayes error.

## Error analysis

* Evaluate multiple performance-improving ideas in parallel (in a table)
* Before fixing incorrectly labelled data, collect statistics and estimate performance gain
* Build your first system quickly, then iterate

## Mismatched training and dev/test set

* Choose a dev set and test set to reflect data you expect to get in the future and consider important to do well on. Also put a part of these data into training set.
* Set up a training-dev set that has the same distribution as training set
  * Large variance between training and training-dev set: overfitting to training set
  * Large variance between training-dev and dev test: data mismatch
* Addressing data mismatch:
  * Manual error analysis
  * Collect more data similar to dev/test set
    * Artificial data synthesis
