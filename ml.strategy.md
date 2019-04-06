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

## Transfer learning

Transfer learning makes sense when
* Task A and B have the same input X
* You have a lot more data for A (pre-training) than B (fine-tuning)
* Low level features from A could be helpful for learning B

## Multi-task learning

Multi-task learning makes sense when
* Training on a set of tasks that could benefit from having shared low-level features
* Usually: amount of data you have for each task is quite similar

$$
\begin{aligned}

Cost &= \frac{1}{m} \sum\limits_{i=1}^m \sum\limits_{j=1}^{n^{[L]}} L(\hat{y}_j^{(i)}, y_j^{(i)}) \\

L &: usually\ logistic\ cross\ entropy\ loss \\

\end{aligned} \\
$$

## End-to-end learning

In contrast to this pipeline with a lot of stages, what end-to-end deep learning does, is you can train a huge neural network to just input the audio clip, and have it directly output the transcript.

One of the challenges of end-to-end deep learning is that you might need a lot of data before it works well.

Multi-step approach works better when:
* Each sub-task you are solving is much simpler
* You have a lot of data for each sub-task

Pros of end-to-end learning:
* Let the data speak
* Less hand-designing of components needed

Cons of end-to-end learning:
* May need large amount of data
* Excludes potentially useful hand-designed components

Applying end-to-end learning
* Key question: do you have sufficient data to learn a function of the complexity needed to map x to y?
