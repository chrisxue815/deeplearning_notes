## Word embeddings

A categorical feature represented as a continuous-valued feature. Typically, an embedding is a translation of a high-dimensional vector into a low-dimensional space.

* Visualizing embeddings in 2D using t-SNE
* Transfer learning
* Embedding matrix: e = E @ o

### Applications

* Useful for named entity recognition, text summarization, co-reference resolution, parsing
* Less useful for language modeling, machine translation, especially if you're accessing a language modeling or machine translation task for which you have a lot of data just dedicated to that task.

### Application in analogy reasoning

Question: A is to A' as B is to what?

$$
arg\max_{w} sim(e_w, e_B - e_A + e_{A'})
$$

where $sim$ is commonly cosine similarity function

$$
sim(u, v) = \frac{u^Tv}{||u||_2 * ||v||_2}
$$

## Learning word embeddings

### Word2Vec skip-gram

* Input: context
* Output: target
* Parameters: E, w, b
* Context/target pairs
  * Last 4 words
  * 4 words on left & right
  * Last 1 word
  * Nearby 1 word

Model:

$$

O_c -> E -> e_c -> softmax -> \hat{y} \\

v = vocab\_size \\

softmax: p(t|c) = \frac{e^{θ_t^T e_c}}{\sum_{j=1}^{v} e^{θ_j^T e_c}} \\

L = - \sum_{i=1}^v y ln(\hat{y}) \\

$$

Problems with softmax classification:
* Summing over vocabulary size is expensive. Solution: Hierarchical softmax.

### Negative sampling

Model:

$$

O_c -> E -> e_c -> v * logistic\ units \\

P(y=1|c,t) = σ(θ_t^T e_c) \\

$$

Training:

* One positive context/word pair, k randomly chosen negative pairs, where the possibility $P(w_i)$ is governed by

$$
P(w_i) = \frac{f(w_i)^{0.75}}{\sum_{j=1}^v f(w_j)^{0.75}}
$$

### GloVe (global vectors for word representation)

* $x_{ij}$ =  # times i appears in context of j

Model:

$$
\sum_{i=1}^v \sum_{j=1}^v f(x_{ij}) (θ_i^T e_j + b_i + b_j' - ln(x_{ij}))^2
$$

where

* $f(x_{ij})$ = 0 if $x_{ij}$ = 0
* $f(x_{ij})$ is smaller if $i$ or $j$ is less frequent
* $f(x_{ij})$ is larger if $i$ or $j$ is more frequent

$θ_i$ and $e_j$ is symmetric. One way to train the algorithm is to initialize $θ_i$ and $e_j$ both uniformly at random, run gradient descent to minimize its objective, and then when you're done for every word, $e_w^{(final)} = \frac{θ_w + e_w}{2}$

## RNN and word embeddings

* Sentiment classification

## Debiasing word embeddings

1. Identify bias direction

$$
average(e_{he} - e_{she} + e_{male} - e_{female} + ...)
$$

average can be replaced by more complex functions like SVD (singular value decomposition)

2. Neutralize: For every word that is not definitional, project to get rid of bias

3. Equalize pairs
