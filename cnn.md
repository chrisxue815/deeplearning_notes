## CNN

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
* Residual network, residual block
* 1x1 convolution, bottleneck layer

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

## Classic networks
* LeNet
* AlexNet
* VGG
* ResNet
* Inception

## ResNet

$$
\begin{aligned}

z^{[l+1]} &= w^{[l+1]} a^{[l]} + b^{[l+1]} \\

a^{[l+1]} &= g(z^{[l+1]}) \\

z^{[l+2]} &= w^{[l+2]} a^{[l+1]} + b^{[l+2]} \\

a^{[l+2]} &= g(z^{[l+2]} + a^{[l]}) \\

\end{aligned} \\
$$

Why do residual networks work?
* Linear function is easy for residual block to learn
* Using a skip-connection helps the gradient to backpropagate and thus helps you to train deeper networks

What you should remember:
* Very deep "plain" networks don't work in practice because they are hard to train due to vanishing gradients.
* The skip-connections help to address the Vanishing Gradient problem. They also make it easy for a ResNet block to learn an identity function.
* There are two main type of blocks: The identity block and the convolutional block.
* Very deep Residual Networks are built by stacking these blocks together.

## Applications

* Object classification, localization, detection
* Face verification, recognition
* Style transfer
