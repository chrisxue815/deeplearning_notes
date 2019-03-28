The main steps for building a Neural Network are:
1. Define the model structure (such as number of input features)
2. Initialize the model's parameters
3. Loop:
    - Calculate current loss (forward propagation)
    - Calculate current gradient (backward propagation)
    - Update parameters (gradient descent)

Input:

$$
\{(x^i, y^i): 1≤i≤m\} \\

\begin{aligned}

x^i &∈ R^n \\
y^i &∈ \{0, 1\} \\

\end{aligned} \\
$$
<br/>

Parameters (weights and bias):

$$
\{w, b\} \\

\begin{aligned}

w &∈ R^n \\
b &∈ R \\

\end{aligned} \\
$$
<br/>

Output / activation function:

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
\begin{aligned}

p(y|x) &= (a^i)^{y^i} (1-a^i)^{1-y^i} \\
L(a^i, y^i) &= -ln(p(y|x)) \\
&= -(y^iln(a^i) + (1-y^i)ln(1-a^i)) \\

\end{aligned} \\
$$
<br/>

Cost function:

$$
J = \frac{1}{m} \sum\limits_{i=1}^m L(a^i, y^i)
$$
<br/>

Gradient descent: <br/>
Repeat <br/>
{

$$
\begin{aligned}

w &:= w - 	α \frac{∂J}{∂w} \\
b &:= b - 	α \frac{∂J}{∂b} \\

\end{aligned} \\
$$
}
<br/>

Backward propagation:

$$
\begin{aligned}

\frac{∂L(a, y)}{∂a} &= -\frac{y}{a} + \frac{1-y} {1-a} \\

\frac{da}{dz} &= \frac{e^{-z}}{(e^{-z}+1)^2} \\
&= \frac{1}{1+e^{-z}}(1-\frac{1}{1+e^{-z}}) \\
&= a(1-a) \\

\frac{∂L(a, y)}{∂z} &= \frac{∂L(a, y)}{∂a}\frac{da}{dz} \\
&= a-y \\

\frac{∂L(a, y)}{∂w_j} &= \frac{∂L(a, y)}{∂z}\frac{dz}{dw_j} \\
&= (a-y)x_j \\

\frac{∂L(a, y)}{∂b} &= \frac{∂L(a, y)}{∂z}\frac{dz}{db} \\
&= a-y \\

\frac{∂J}{∂w_j} &= \frac{1}{m} \sum\limits_{i=1}^m \frac{∂L(a^i, y^i)}{∂w_j} \\
&= \frac{1}{m} \sum\limits_{i=1}^m (a^i-y^i)x^i_j \\

\frac{∂J}{∂b} &= \frac{1}{m} \sum\limits_{i=1}^m \frac{∂L(a^i, y^i)}{∂b} \\
&= \frac{1}{m} \sum\limits_{i=1}^m (a^i-y^i) \\

\end{aligned} \\
$$
<br/>

$$
\begin{aligned}

\end{aligned} \\
$$
<br/>

Overfitting:

Try to increase the number of iterations. You might see that the training set accuracy goes up, but the test set accuracy goes down. This is called overfitting.
