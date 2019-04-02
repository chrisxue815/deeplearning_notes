## Normalizing inputs

$$
\begin{aligned}

mean\ μ &= \frac{1}{m} \sum\limits_{i=1}^m x^{(i)} \\
x -&= μ \\
variance\ σ^2 &= \frac{1}{m} \sum\limits_{i=1}^m (x^{(i)} - μ)^2 ...... μ=0\ here \\
x /&= σ^2 \\

\end{aligned} \\
$$

## Weight initialization

Deep networks suffer from vanishing / exploding gradients.

Partial solution: carefully choosing how you initialize weights helps a lot.

The larger $n^{[l]}$ is, the smaller $w^{[l]}$ should be.

$$
\begin{aligned}

target\ variance\ σ^2(w)
&= \frac{1}{n^{[l]}} \\
&= \frac{2}{n^{[l]}} ...... for\ ReLU \\
&= \sqrt{\frac{1}{n^{[l-1]}}} ...... for\ tanh \\

w^{[l]} &= np.random.randn(shape) * np.sqrt(σ^2) \\

\end{aligned} \\
$$
