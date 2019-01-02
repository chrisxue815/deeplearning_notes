Input:

$$
\{(x^i, y^i): 1≤i≤m\} \\

\begin{aligned}

x^i &∈ R^n \\
y^i &∈ \{0, 1\} \\

\end{aligned} \\
$$
<br/>

Parameters:

$$
\{w, b\} \\

\begin{aligned}

w &∈ R^n \\
b &∈ R \\

\end{aligned} \\
$$
<br/>

Output:

$$
\begin{aligned}

\hat{y}^i &= a^i \\
&= σ(z^i) \\
&= \frac{1}{1 + e^{-z^i}} \\

z^i &= w^T x^i + b \\
&= (\sum\limits_{j=1}^n w_j x^i_j) + b

\end{aligned} \\
$$
<br/>

Loss function (cross entropy):

$$
L(a^i, y^i) = -(y^iln(a^i) + (1-y^i)ln(1-a^i))
$$
<br/>

Cost function:

$$
J(w, b) = \frac{1}{m} \sum\limits_{i=1}^m L(a^i, y^i)
$$
<br/>

Gradient descent: <br/>
Repeat <br/>
{

$$
\begin{aligned}

w &:= w - 	α \frac{∂J(w, b)}{∂w} \\
b &:= b - 	α \frac{∂J(w, b)}{∂b} \\

\end{aligned} \\
$$
}
<br/>

Backward propagation:

$$
\begin{aligned}

\frac{∂L(a, y)}{∂a} &= -\frac{y}{a} + \frac{1-y} {1-a} \\

\frac{∂a}{∂z} &= \frac{e^{-z}}{(e^{-z}+1)^2} \\
&= \frac{1}{1+e^{-z}}(1-\frac{1}{1+e^{-z}}) \\
&= a(1-a) \\

\frac{∂L(a, y)}{∂z} &= \frac{∂L(a, y)}{∂a}\frac{∂a}{∂z} \\
&= a-y \\

\frac{∂L(a, y)}{∂w_j} &= \frac{∂L(a, y)}{∂z}\frac{∂z}{∂w_j} \\
&= (a-y)x_j \\

\frac{∂L(a, y)}{∂b} &= \frac{∂L(a, y)}{∂z}\frac{∂z}{∂b} \\
&= a-y \\

\frac{∂J(a, y)}{∂w_j} &= \frac{1}{m} \sum\limits_{i=1}^m \frac{∂L(a^i, y^i)}{∂w_j} \\
&= \frac{1}{m} \sum\limits_{i=1}^m (a^i-y^i)x^i_j

\end{aligned} \\
$$
<br/>

$$
\begin{aligned}

\end{aligned} \\
$$
<br/>
