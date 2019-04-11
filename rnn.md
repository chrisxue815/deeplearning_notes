## Why not a standard network?

* Inputs, outputs can be different lengths in different examples
* Doesn't share features learned across different positions of text

## Concepts

* Ont-hot encoding
* Encoder, decoder

Forward propagation

$$
\begin{aligned}

a^{<t>} &= g(W_a [a^{<t-1>}, x^{<t>}] + b_a) \\

\hat{y}^{<t>} &= g'(W_y a^{<t>} + b_y) \\

L^{<t>} &= -(y^{<t>} ln(\hat{y}^{<t>}) + (1 - y^{<t>}) ln(1-\hat{y}^{<t>})) \\

L &= \sum_{t=1}^{T_x} L^{<t>} \\

\end{aligned} \\
$$

Commonly, g is tanh, g' is sigmoid or softmax

## Applications

* Many-to-many ($T_x = T_y$)
  * Name entity recognition
  * DNA sequence analysis
* Many-to-many ($T_x ≠ T_y$)
  * Speech recognition
  * Machine translation
* One-to-many ($T_x = 1$)
  * Music generation
* Many-to-one ($T_y = 1$)
  * Sentiment classification
  * Video activity recognition
* Attention-based

## Language model

* Output:

$$
\begin{aligned}

P(sentence) &= P(y^{<1>}, y^{<2>}, y^{<3>}, ..., y^{<T_y>}) \\
&= P(y^{<1>}) * P(y^{<2>}|y^{<1>}) * P(y^{<3>}|y^{<1>}, y^{<2>}) * ... * P(y^{<T_y>}|y^{<1>}, ..., y^{<T_y-1>})

\end{aligned} \\
$$

* Training set: a large corpus of texts
* Training: same as RNN, where

$$
\begin{aligned}

x^{<1>} &= 0 \\
x^{<t>} &= y^{<t-1>} \\

\end{aligned} \\
$$

* Sampling (generating): same as RNN, where

$$
\begin{aligned}

x^{<1>} &= 0 \\
x^{<t>} &= np.random.choice(vocabulary, p=\hat{y}^{<t-1>}) \\

\end{aligned} \\
$$

* Loss function: softmax of $y$ and $\hat{y}$
* Word-level, character-level

## Exploding gradient

* Gradient clipping

## Vanishing gradient

### Gated recurrent unit (GRU)

$$
\begin{aligned}

\tilde{c}^{<t>} &= tanh(W_c [Γ_r * c^{<t-1>}, x^{<t>}] + b_c) \\

Γ_u &= σ(W_u [c^{<t-1}, x^{<t>}] + b_u) \\

Γ_r &= σ(W_r [c^{<t-1}, x^{<t>}] + b_r) \\

c^{<t>} &= Γ_u * \tilde{c}^{<t>} + (1 - Γ_u) * c^{<t-1>} \\

a^{<t>} &= c^{<t>} \\

\end{aligned} \\
$$

### LSTM

$$
\begin{aligned}

\tilde{c}^{<t>} &= tanh(W_c [a^{<t-1>}, x^{<t>}] + b_c) \\

Γ_u &= σ(W_u [a^{<t-1}, x^{<t>}] + b_u) \\

Γ_f &= σ(W_f [a^{<t-1}, x^{<t>}] + b_f) \\

Γ_o &= σ(W_o [a^{<t-1}, x^{<t>}] + b_o) \\

c^{<t>} &= Γ_u * \tilde{c}^{<t>} + Γ_f * c^{<t-1>} \\

a^{<t>} &= Γ_o * tanh(c^{<t>}) \\

\end{aligned} \\
$$

* $c$ = memory cell
* $Γ$ = gate
* $u$ = update
* $r$ = relevance
* $f$ = forget
* $o$ = output

Common variance: peephole connection

## Bidirectional RNN (BRNN)

$$
\begin{aligned}

\overrightarrow{a}^{<t>} &= g(W_{\overrightarrow{a}} [a^{<t-1>}, x^{<t>}] + b_{\overrightarrow{a}}) \\

\overleftarrow{a}^{<t>} &= g(W_{\overleftarrow{a}} [a^{<t+1>}, x^{<t>}] + b_{\overleftarrow{a}}) \\

\hat{y}^{<t>} &= g'(W_y [\overrightarrow{a}^{<t>}, \overleftarrow{a}^{<t>}] + b_y) \\

\end{aligned} \\
$$

## Deep RNN

$$
\begin{aligned}

a^{[l]<t>} &= g(W_a^{[l]} [a^{[l]<t-1>}, x^{[l-1]<t>}] + b_a^{[l]}) \\

\hat{y}^{<t>} &= g'(W_y a^{[L]<t>} + b_y) \\

\end{aligned} \\
$$

## What you should remember

- A sequence model can be used to generate musical values, which are then post-processed into midi music.
- Fairly similar models can be used to generate dinosaur names or to generate music, with the major difference being the input fed to the model.
- In Keras, sequence generation involves defining layers with shared weights, which are then repeated for the different time steps $1, \ldots, T_x$.
