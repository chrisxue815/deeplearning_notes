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

## Gradient descent with momentum

Compute dw and db.

$$
\begin{aligned}

v_{dw} &= β v_{dw} + (1 - β) dw \\

w -&= α v_{dw} \\

\end{aligned} \\
$$

The same applies to b.

## RMSprop

Compute dw and db.

$$
\begin{aligned}

s_{dw} &= β v_{dw} + (1 - β) dw^2 \\

w -&= \frac{α dw}{\sqrt{s_{dw}} + ε} \\

ε &= 10^{-8}

\end{aligned} \\
$$

The same applies to b.

## Adam (Adaptive momentum estimation)

On iteration t:

Compute dw and db.

$$
\begin{aligned}

v_{dw} &= β_1 v_{dw} + (1 - β_1) dw \\

s_{dw} &= β_2 s_{dw} + (1 - β_2) dw^2 \\

v_{dw} &= \frac{v_{dw}}{1 - β_1^t} \\

s_{dw} &= \frac{s_{dw}}{1 - β_2^t} \\

w -&= \frac{α v_{dw}}{\sqrt{s_{dw}} + ε}

\end{aligned} \\
$$

Common hyperparameter choices:

$$
\begin{aligned}

α &= needs\ to\ be\ tuned \\

β_1 &= 0.9 \\

β_2 &= 0.999 \\

ε &= 10^{-8}

\end{aligned} \\
$$

Larger β = larger momentum

## Learning rate decay

Inverse time decay:

$$
α = α_0 * \frac{1}{1 + decay\_rate * epoch\_num}
$$

Exponential decay:

$$
α = α_0 * decay\_rate ^ {epoch\_num}
$$

## Challenges for optimization algorithms

* In high dimensional space, it's unlikely to get stuck in a bad local optima. Instead most points of zero gradient are saddle points.
* Plateaus can make learning slow.
