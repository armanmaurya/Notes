---
tags:
  - AI
  - ML
aliases:
  - Deep Learning Transformers
---
The paper 'Attention Is All You Need' introduces a architecture called Transformer. We use [Attention-Mechanism](Attention%20Mechanism.md). Like LSTM, Transformer is an architecture for transforming one sequence into another one with the help of two parts (Encoder and Decoder).

See BERT: Bidirectional Transformers.![](Images/1_BHzGVskWGS_3jEcYYi6miQ.webp)
The Encoder is on the left and Decoder is on the right. Both Encoder and Decoder are composed of modules that can be stacked on top of each other multiple times, which described by $Nx$ in the figure. We see that the modules consists mainly of Multi-Head Attention and Feed Forward layers. The input and the output (target sentences) are first embedded into an n-dimensional space since we cannot use strings directly.

One slight but important part of the model is the positional encoding of the different words. Since we have no recurrent networks that can remember how sequences are fed into a model, we need to somehow give every word/part in our sequence a relative position since a sequence depends on representation (n-dimensional vector) of each word.