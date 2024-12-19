---
tags:
  - Maths
  - Matrix
---
Let A be any $m\times n$ [Matrix](Matrices.md). It has square sub-matrices of different orders. The determinants of these square sub-matrices are called minors of A.

A matrix **A** is said to be of rank $r$ if 
1. It has at least one non-zero minor of order $r$.
2. All the minors of order $(r+1)$ or higher than $r$ are zero.

Symbolically, **rank** of $A=r$ is written as $\rho(A)=r$.
From the definition of the rank of a matrix A, it follows that:
1. If $A$ is a null matrix, then $\rho(A)=0$.
2. If $A$ is not a null matrix, then $\rho(A)\geq 1$.
3. If $A$ is a [Non-Singular](Non-Singular%20Matrix.md) $n\times n$ matrix, then $\rho(A)=n$.
4. If $I_{n}$ is the $n\times n$ [Identity Matrix](Identity%20Matrix.md), then $|I_{n}|=1\ne0\implies \rho(I_{n})=n$.
5. If **A** is an $m\times n$ matrix then, $\rho(A)\leq \text{minimum of m and n}.$.
6. If all minors of order $r$ are equal to zero, then $\rho(A)<r$.

---
Related Links:-
- [Methods Of Finding Rank](Methods%20Of%20Finding%20Rank.md)