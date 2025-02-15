---
aliases:
  - Transfromers Attention Mechanism
tags:
  - Attentation
---
# Overview
The attention mechanism was introduced to improve the performance of the encoder-decoder model for machine translation. The idea behind the attention mechanism was to permit the decoder to utilize the most relevant parts of the input sequence in a flexible manner, by a weighted combination of all the encoded input vectors, with the most relevant vectors being attributed the highest weights.

# The Attention Mechanism 
The attention mechanism was introduced to address the bottleneck problem that arises with use of a fixed-length encoding vector, where the decoder would have limited access to the information provided by the input. This is through to become especially problematic for long or complex sequence, where the dimensionality of their representation would be forced to the same as for shorter or simpler sequences.

Attention Mechanism is divided into the step-by-step computations of the alignment scores, the weights, and the context vector:
1. **Alignment scores:** The alignment model takes the encoded hidden states, $h_{i}$ and the previous decoder output, $s_{t-1}$ to compute a score, $e_{t,i}$, that indicates how well the elements of the input sequence align with the current output at the position, $t$. The alignment model is represented by a function, $a(.)$ which can be implemented by a feedforward neural network: $$e_{t,i} = a(s_{t-1}, h_{i})$$
2. **Weights:** The weights, $a_{t,i}$, are computed by applying a softmax operation to the previously computed alignment scores: $$\alpha_{t,i} = \text{softmax}(e_{t,i})$$
3. **Context vector:** A unique context vector, $c_{t}$, is fed into the decoder at each time step. It is computed by a weighted sum of all, $T$, encoder hidden states: $$c_{t} = \Sigma_{i=1}^T \alpha_{t,i}h_{i}$$
However, the attention mechanism can be re-formulated into a general form that can be applied to any sequence-to-sequence task, where information may not necessarily be related in a sequential fashion.

# The General Attention Mechanism 
The general attention mechanism makes use of three main components, namely the queries Q, the keys K, and the values V.
