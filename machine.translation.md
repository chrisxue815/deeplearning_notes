## Encoder-decoder model

Also called "conditional language model"

Objective:

$$
arg\max_{y^{<1>},...,y^{<T_y>}} P(y^{<1>},...,y^{<T_y>}|x)
$$

## Beam search

* Hyperparameter beam width $B$.
* Considers B highest possibilities at a time

Objective:

$$
arg\max_y \prod_{t=1}^{T_y} P(y^{<t>}|x, y^{<1>}, ..., y^{<t-1>})
$$

## Length normalization

Normalized log likelyhood objective:

$$
arg\max_y \frac{1}{T_y^α} \sum_{t=1}^{T_y} log P(y^{<t>}|x, y^{<1>}, ..., y^{<t-1>}) \\
$$

## Error analysis

Given human result $y^*$ and algorithm result $\hat{y}$,

* If $P(y^*) > P(\hat{y})$, beam search is at fault
* If $P(y^*) < P(\hat{y})$, RNN model is at fault

## Bleu score

Bleu = Bilingual evaluation understudy

$$
\begin{aligned}

Bleu\ score = BP * exp(\frac{1}{m} \sum_{n=1}^m P_n) \\

BP = Brevity\ penalty \\

P_n = \frac{\sum_{ngram ∈ \hat{y}} Count_{clip}(ngram)}{\sum_{ngram ∈ \hat{y}} Count(ngram)} \\

\end{aligned} \\
$$

## Attention model

$$
\begin{aligned}

a^{<t'>} = (\overrightarrow{a}^{<t'>}, \overleftarrow{a}^{<t'>}) \\

c^{<t>} = \sum_{t'} α^{<t,t'>} a^{<t'>} \\

α^{<t,t'>} = softmax(e^{<t,t'>}) \\

e^{<t,t'>} = NN(s^{<t-1>}, a^{t'}) \\

\end{aligned} \\
$$

where
* $c$ = context
* $α^{<t,t'>}$ = amount of attention $y^{<t>}$ should pay to $a^{<t'>}$
* $e$ = energy
