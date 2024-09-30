The **outer product** is a specific type of matrix operation, commonly applied to two vectors (as opposed to matrices in the Kronecker product). If you have two vectors $( u )$ and $( v )$, their outer product results in a matrix, where each element of the matrix is the product of an element from $( u )$ and an element from $( v )$.
### Definition:
Let $\left( u \in \mathbb{R}^m \right)$ be a column vector and $\left( v \in \mathbb{R}^n \right)$ be a row vector. The **outer product** of $( u )$ and $( v )$, denoted as $( u \otimes v )$ (or simply $( uv^T )$ for vectors), results in an $( m \times n )$ matrix.

$$\left[
U = \begin{bmatrix} u_1 \\ u_2 \\ \vdots \\ u_m \end{bmatrix}, \quad v = \begin{bmatrix} v_1 \\ v_2 \\ \dots \\ v_n \end{bmatrix}
\right]$$
# Outer Product
The outer product $\left( u \otimes v \right)$ (or $( uv^T )$) is:

$$\left[
U \otimes v = \begin{bmatrix}
U_1 v_1 & u_1 v_2 & \dots & u_1 v_n \\
U_2 v_1 & u_2 v_2 & \dots & u_2 v_n \\
\vdots & \vdots & \ddots & \vdots \\
U_m v_1 & u_m v_2 & \dots & u_m v_n
\end{bmatrix}
\right]$$
### Example:
Let $\left( u = \begin{bmatrix} 1 \\ 2 \end{bmatrix} \right)$ and $\left( v = \begin{bmatrix} 3 \\ 4 \\ 5 \end{bmatrix} \right)$.
The outer product $\left( u \otimes v \right)$ is:
$$\left[
U \otimes v = \begin{bmatrix}
1 \cdot 3 & 1 \cdot 4 & 1 \cdot 5 \\
2 \cdot 3 & 2 \cdot 4 & 2 \cdot 5
\end{bmatrix}
= \begin{bmatrix}
3 & 4 & 5 \\
6 & 8 & 10
\end{bmatrix}
\right]$$
### Differences Between Kronecker and Outer Product:
- **Kronecker product** is defined for two matrices and results in a block matrix.
- **Outer product** is typically defined for two vectors and results in a matrix. It is a specific case of the Kronecker product when the two inputs are vectors.

---
**Related Links:**
- [Matrices](Matrices.md)