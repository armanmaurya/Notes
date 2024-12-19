---
tags:
  - Maths
  - Matrix
---
Two [Matrices](Matrices.md) A and B are said to be conformable for the product AB **(in this very order of A and B)** if the ~={cyan}number of columns in A=~ (called the pre-factor) is ~={yellow}equal=~ to the ~={cyan}number of rows in B=~ (called the post-factor).

Thus, if the order of A and B are $m\times n$ and $p\times q$ respectively, then
1. AB is defined if number of columns in A = number of rows in B, $i.e.,$ if $n=p$
2. BA is defined if number of columns in B = number of rows in A, $i.e.,$ if $q=m$

Let $A=[a_{ij}]_{m\times n}$, and $B=[b_{ij}]_{n\times p}$ be two [Matrices](Matrices.md) conformable for the product AB, then 
AB is defined as the matrix $C=[c_{ij}]_{m\times p}$, 

where $c_{ij} =a_{i1}b_{1j}+a_{i2}b_{2j}+\dots+a_{in}b_{nj}=\sum_{k=1}^n a_{ik}b_{kj}$
$i.e.,$ $\quad \quad (i,j)^{th}$ element of AB = sum of the products of the elements of $i^{th}$ row of A with the corresponding elements of $j^{th}$ column of B.

The rule for multiplication of two conformable matrix is called **row-by-column method**.
## Properties
1. Matrix multiplication is not commutative in general $i.e.,$ $AB \ne BA$
2. Matrix multiplication is associative $i.e.,$ $(AB)C=A(BC)$.
3. Matrix multiplication is distribution with respect to matrix addition $i.e.,$ $$A(B+C)=AB+AC$$
4. If A and I are square Matrices of the same order, then AI = IA = A.
5. If A is a square matrix of order $n$, then $A\times A=A^2$, $A\times A\times A=A^3$, $A\times A\times A\dots m$ times = $A^m$ are all square matrices of order $n$.
   Also, we define $A^\text{o}=I$.
6. For any positive integer $n, I^n=I$.