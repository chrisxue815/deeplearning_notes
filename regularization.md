## L2 regularization

$$
\begin{aligned}

J &= \frac{1}{m} \sum\limits_{i=1}^m L^{(i)} + \frac{λ}{2m} \sum\limits_{l=1}^m ||w^{[l]}||^2_{F} \\

Forbenius\ norm\ ||w^{[l]}||^2_F &= \sum\limits_{i=1}^{n^{[l]}} \sum\limits_{j=1}^{n^{[l-1]}} (w^{[l]}_{ij})^2 \\

dw^{[l]} &= (from\ backprop) + \frac{λ}{m} w^{[l]} \\

w^{[l]}
&= w^{[l]} - αdw^{[l]} \\
&= (1 - \frac{αλ}{m}) w^{[l]} - α(from\ backprop) \\

\end{aligned}
$$

which is why L2 regularization is also called "weight decay".
