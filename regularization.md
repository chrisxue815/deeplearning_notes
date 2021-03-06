﻿## L2 regularization

$$
\begin{aligned}

J &= \frac{1}{m} \sum_{i=1}^m L^{(i)} + \frac{λ}{2m} \sum_{l=1}^m ||w^{[l]}||^2_{F} \\

Forbenius\ norm\ ||w^{[l]}||^2_F &= \sum_{i=1}^{n^{[l]}} \sum_{j=1}^{n^{[l-1]}} (w^{[l]}_{ij})^2 \\

dw^{[l]} &= (from\ backprop) + \frac{λ}{m} w^{[l]} \\

w^{[l]}
&= w^{[l]} - αdw^{[l]} \\
&= (1 - \frac{αλ}{m}) w^{[l]} - α(from\ backprop) \\

\end{aligned}
$$

which is why L2 regularization is also called "weight decay".

## Dropout

Training (inverted dropout):

$$
\begin{aligned}

d^{[l]} &= np.random.rand(*a^{[l]}.shape) < keep\_prob^{[l]} \\

a^{[l]} *&= d^{[l]} \\

a^{[l]} *&= \frac{1}{keep\_prob^{[l]}} \\

\end{aligned}
$$

Predicting:

No dropout.

Downside:

Cost function J is no longer well defined. You lose the debugging tool of plotting cost function graph. You can mitigate this downside by turning off dropout temporarily.

## Other tricks

* Data augmentation
  * Mirroring
  * Random cropping
  * Color shifting, PCA color augmentation
  * Implementing distortions during training
* Early stopping
  * Comparing to L2 regularization, pro: no need to tune hyperparameter λ
  * con: against orthogonalization
* Ensembling: Train several networks independently and average their outputs
* Multi-crop at test time: Run classifier on multiple versions of test images and average results
