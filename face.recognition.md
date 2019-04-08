* Face verification: 1:1 matching
* Face recognition: 1:K matching
* One shot learning
* Learning a similarity function $d(img1, img2)$ = degree of difference between images

## DeepFace, siamese network

* Parameters of NN define an encoding/embedding $f(x^{(i)})$
* Distance $d(x^{(i)}, x^{(j)}) = ||f(x^{(i)} - x^{(j)})||^2$
* Learn parameters so that:
  * If $x^{(i)}$ and $x^{(j)}$ are the same person, $d(x^{(i)}, x^{(j)})$ is small.
  * If $x^{(i)}$ and $x^{(j)}$ are the different persons, $d(x^{(i)}, x^{(j)})$ is large.

## FaceNet, triplet loss

Goal

$$
d(A, P) + α ≤ d(A, N)
$$

where $α$ is a margin

Loss function

$$
\begin{aligned}
L &= max(0, d(A, P) - d(A, N) + α) \\
Cost &= \sum\limits_{i=1}^m L^{(i)}
\end{aligned} \\
$$

Choose triplets that are hard to train on.

$$
d(A, P) ≈ d(A, N)
$$

## Face verification and binary classification

$$
\begin{aligned}

\hat{y} &= σ (w * d(i, j) + b) \\

L1\ similarity:\ d(i, j) &= |f(x^{(i)}) - f(x^{(j)})| \\

χ2\ similarity:\ d(i, j) &= \frac{(f(x^{(i)}) - f(x^{(j)}))2} {f(x^{(i)}) + f(x^{(j)})}

\end{aligned} \\
$$
