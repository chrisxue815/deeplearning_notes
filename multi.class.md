## Softmax activation

Forward propagation:

$$
\begin{aligned}

z^{[L]} &= w^{[L]} a^{[L-1]} + b^{[L]} \\

t &= e^{z^{[L]}} \\

a^{[L]} &= \frac{t}{\sum_{j=1}^{n_L} t_j} \\

L &= -\sum_{j=1}^{n_L} y_j log(a^{[L]}_j) \\

J &= \frac{1}{m} \sum_{i=1}^m L^{(i)} \\

\end{aligned} \\
$$

Backward propagation:

$$
\begin{aligned}

dz^{[L]} &= a^{[L]} - y \\

\end{aligned} \\
$$
