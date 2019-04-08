## What are deep ConvNets learning?

Visualizing and understanding convolutional networks
* Pick a unit in layer 1. Find the 9 image patches that maximize the unit's activation.
* Repeat for other units

## Cost function

$$
J(G) = α J_{content}(C, G) + β J_{style}(S, G)
$$

Find the generated image G
1. Initialize G randomly
1. Use gradient descent to minimize J(G)

### Content cost function

$$
J_{content}(C, G) = \frac{1}{2} ||a^{[l](C)} - a^{[l](G)}||^2
$$

### Style cost function
* Define style as correlation between activations across channels
* Let $a_{i,j,k}^{[l]}$ = activation at $(i,j,k)$
* Style matrix (gram matrix) $G^{[l]}$ is $n_c^{[l]} * n_c^{[l]}$

$$
G_{k,k'}^{[l]} = \sum\limits_{i=1}^{n_H^{[l]}} \sum\limits_{j=1}^{n_W^{[l]}} a_{i,j,k}^{[l]} a_{i,j,k'}^{[l]} \\

(unnormalized\ cross-covariance)
$$

* Style cost function:

$$
\begin{aligned}

J_{style}^{[l]}(S, G)
&= \frac{1}{2 n_H^{[l]} n_W^{[l]} n_c^{[l]}} ||G^{[l](S)} - G^{[l](G)}||_F^2 \\
&= \frac{1}{2 n_H^{[l]} n_W^{[l]} n_c^{[l]}} \sum\limits_k \sum\limits_{k'} (G_{k,k'}^{[l](S)} - G_{k,k'}^{[l](G)})^2 \\

J_{style}(S, G) &= \sum\limits_l λ^{[l]} J_{style}^{[l]}(S, G) \\

\end{aligned} \\
$$