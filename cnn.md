## Concepts

* Convolution, cross-correlation
* Max pooling, average pooling
* Fully connected layer
* Padding
  * Valid padding: no padding
  * Same padding: pad so that output size is the same as the input size
* Stride
* Output size

$$
⌊ \frac{n + 2p - f}{s} + 1 ⌋
$$

* Why convolution
  * Parameter sharing: a feature detector (such as a vertical edge detector) that's useful in one part of the image is probably useful in another part of the image
  * Sparsity of connections: in each layer, each output value depends only on a small number of inputs
* Translation invariance

## Forward propagation

$$
\begin{aligned}

n_H^{[l]} &= \lfloor \frac{n_H^{[l-1]} + 2p^{[l]} - f^{[l]}}{s} + 1 \rfloor \\

\end{aligned} \\
$$

The same applies to $n_W$.

$$
\begin{aligned}

z^{[l]} &= w^{[l]} * a^{[l-1]} + b^{[l]} \\

\end{aligned} \\
$$

Dimension:

$$
\begin{aligned}

(m, n_H^{[l]}, n_W^{[l]}, n_C^{[l]})

&= (f^{[l]}, f^{[l]}, n_C^{[l-1]}, n_C^{[l]})

* (m, n_H^{[l-1]}, n_W^{[l-1]}, n_C^{[l-1]})

+ (1, 1, 1, n_C^{[l]})\\

\end{aligned} \\
$$
