Forward propagation:

$$
\begin{aligned}

z^{[l]} &= w^{[l]} a^{[l-1]} + b^{[l]} \\

Dimension: \frac{n^{[l]}}{m} &= \frac{n^{[l]}}{n^{[l-1]}} \frac{n^{[l-1]}}{m} + \frac{n^{[l]}}{1} \\

a^{[l]} &= g(z^{[l]}) \\

L &= - (yln(a^{[l]}) + (1-y)ln(1-a^{[l]}) \\

J &= \frac{1}{m} \sum\limits_{i=1}^m L^{(i)} \\

\end{aligned}
$$

Backward propagation (simplified):

$$
\begin{aligned}

da^{[L]} &= -\frac{y}{a^{[L]}} + \frac{1-y}{1-a^{[L]}} \\

dz^{[l]} &= da^{[l]} g'(z^{[l]}) \\

dw^{[l]} &= \frac{1}{m} dz^{[l]} a^{[l-1]T} \\

Dimension: \frac{n^{[l]}}{n^{[l-1]}} &= \frac{n^{[l]}}{m} \frac{m}{n^{[l-1]}} \\

db^{[l]} &= \frac{1}{m} sum(dz^{[l]}) \\

da^{[l-1]} &= w^{[l]T} dz^{[l]} \\

\end{aligned}
$$

Backward propagation (in detail):

$$
\begin{aligned}

\frac{dL}{da^{[L]}}
&= -\frac{y}{a^{[L]}} + \frac{1-y}{1-a^{[L]}} \\

\frac{dL}{dz^{[l]}}
&= \frac{dL}{da^{[l]}} \frac{da^{[l]}}{dz^{[l]}} \\

\frac{dL}{dw^{[l]}}
&= \frac{dL}{dz^{[l]}} \frac{dz^{[l]}}{dw^{[l]}} \\
&= \frac{dL}{dz^{[l]}} a^{[l-1]} \\

\frac{dL}{db^{[l]}}
&= \frac{dL}{dz^{[l]}} \frac{dz^{[l]}}{db^{[l]}} \\
&= \frac{dL}{dz^{[l]}} \\

\frac{dL}{da^{[l-1]}}
&= \frac{dL}{dz^{[l]}} \frac{dz^{[l]}}{da^{[l-1]}} \\
&= \frac{dL}{dz^{[l]}} w^{[l]} \\

\end{aligned}
$$
