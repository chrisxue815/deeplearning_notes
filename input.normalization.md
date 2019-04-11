## Input normalizing

$$
\begin{aligned}

μ &= \frac{1}{m} \sum_{i=1}^m x^{(i)} \\

x -&= μ \\

σ^2 &= \frac{1}{m} \sum_{i=1}^m (x^{(i)})^2 \\

x /&= \sqrt{σ^2 + ε} \\

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

## Batch normalization

Forward propagation:

$$
\begin{aligned}

z^{[l]} &= w^{[l]} a^{[l-1]} ......b\ omitted \\

μ &= \frac{1}{m} \sum_{i=1}^m z^{(i)} \\

z -&= μ \\

σ^2 &= \frac{1}{m} \sum_{i=1}^m (z^{(i)})^2 \\

z_{norm} &= \frac{z}{\sqrt{σ^2 + ε}} \\

\tilde{z} &= γ z_{norm} + β \\

a &= g(\tilde{z}) \\

\end{aligned} \\
$$

Backward propagation:

$$
\begin{aligned}

da^{[L]} &= -\frac{y}{a^{[L]}} + \frac{1-y}{1-a^{[L]}} \\

d\tilde{z} &= da * g'(\tilde{z}) \\

dγ &= d\tilde{z} * z_{norm} \\

dβ &= d\tilde{z} \\

dz &= \frac{d\tilde{z} * γ}{\sqrt{σ^2 + ε}} \\

dw &= dz * a^{[l-1]} \\

da^{[l-1]} &= dz^{[l]} * w^{[l]} \\

\end{aligned} \\
$$
