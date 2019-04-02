## Mini batch gradient descent

Split training set into mini batches and use one mini batch in one gradient descent iteration.

1 epoch = 1 pass through the entire training set

## Exponentially weighted average

$$
\begin{aligned}

v_t &= β v_{t-1} + (1 - β) θ_t \\

&=
(1 - β) θ_t
+ (1 - β) β θ_{t-1}
+ (1 - β) β^2 θ_{t-2}
+ (1 - β) β^{t-1} θ_1 \\

β ^ {\frac{1}{1 - β}} &= \frac{1}{e} \\

n &= \frac{1}{1 - β} \\

v_t &≈ \frac{1}{n} \sum_{i=t-n}^{t} θ_i ...... average\ over\ the\ last\ n\ data \\

\end{aligned} \\
$$

Bias correction:

$$
\begin{aligned}

v_t &= \frac{v_t}{1 - β^t} \\

\end{aligned} \\
$$
