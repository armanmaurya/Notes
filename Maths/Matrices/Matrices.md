---
tags:
  - Maths
---
- [[#Definition]]
- [[#Types of Matrix]]
	- [[#^7aa97a|Row Matrix]]
	- [[#^dca9d0|Column Matrix]]
	- [[#^1f4168|Square Matrix]]
	- [[#^c5bbb3|Identity or Unit Matrix]]
	- [[#^af8b01|Diagonal Matrix]]
	- [[#^bf0e9f|Upper Triangular Matrix]]
	- [[#^269f61|Lower Triangular Matrix]]
	- [[#^da8333|Symmetric Matrix]]
	- [[#^bf8b8d|Skew-Symmetrix Matrix]]
- [[#Elementary Operations]]
- [[#Inverse of a Matrix by Elementary Transformation]]
- [[#Co-Factor of Matrix]]
- [[#Adjoint of A Square Matrices]]
- [[#Transpose of Matrix]]
# Definition
If `mn` number real or arranged in the form of a rectangular array `A` having `m` rows and `n` columns then `A` is called an $m\times n$ matrix.
# Types of Matrix
1. **Row Matrix:-**
   Matrix having only 1 row and any number of columns.
   E.g. $\begin{bmatrix}2 & 6 & 7 & 8 & 9 & 10\end{bmatrix}$
    ^7aa97a
2.  **Column Matrix:-**
   Matrix having only 1 column and any number of rows.
   E.g. $\begin{bmatrix}1 \\ 2 \\ 2\end{bmatrix}$ ^dca9d0
3. **Square Matrix:**
   Same no of rows & columns
   E.g. $\begin{bmatrix}1 & 2 \\ 3 & 4\end{bmatrix}$ ^1f4168
4. **Identity or Unit Matrix:-**
   A square matrix `A` is said to be identify matrix if it's all the diagonal elements are $1$ and all non-diagonal element are 'o'. ^c5bbb3
   <div style="page-break-after: always;"></div>
1. **Diagonal Matrix:-**
   A square matrix whose each non-diagonal elements are $0$ is called diagonal matrix
   E.g. $\begin{bmatrix}1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3\end{bmatrix}$ ^af8b01
6. **Upper Triangular Matrix:**
   A Square matrix whose all the elements below the principle diagonal are zero is called an upper triangular matrix.
   E.g. $\begin{bmatrix}1 & 2 & 5 \\ 0 & 2 & 4 \\ 0 & 0 & 3\end{bmatrix}$ ^bf0e9f
7. **Lower Triangular Matrix:**
   A square matrix whose all the elements above the principle diagonal are zero is called an lower triangular matrix. ^269f61
8. **Singular & Non-Singular Matrix:-**
   A Square matrix `A` is said to be,
	   1. Singular matrix if $\mid A \mid = 0$
	   2. Non-Singular if $\mid A\mid \ne 0$
9. **Symmetric Matrix:-**
   A Square matrix 'A' is said to be symmetric matrix if $A' = A$ or $a_{ij} = a_{ji} \quad \forall \quad i \ \& \  j$
   E.g. $\begin{bmatrix}1 &-1 & 2 \\ -1 & 5 & 0 \\  2 & 0 & 7\end{bmatrix}$ ^da8333
10. **Skew-Symmetrix Matrix:**
    A Square matrix ' $A$ ' is said to be skew symmetric matrix if $A' =-A$
    $$a_{ij} =-a_{ji} \quad \forall \quad i 
    \& j$$
    If $j$ = i,
    $$a_{ii} =-a_{ii}$$
    $$a_{ii} + a_{ii} = 0$$
    $$2a_{ii} = 0$$
    $$a_{ii} = 0$$
    So all the diagonal elements of Skew-Symmetrix matrix must be **zero**    ^bf8b8d

# Elementary Operations:
Elementary transformation are anyone of the following operations on a matrix:-
- Interchange of any two rows (columns) of a matrix.
  Generally $R_{i} \leftrightarrow R_{j}$ is used for the interchange of the $i^{th}$ and $j^{th}$ row.
- Multiplication of the elements of any row (column) by a non-zero number $k$.
  Generally $R_{i}\to kR_{i}$ is used for the multiplication of the elements of the $i^{th}$ row
- Addition of $k$ time of a row (column) to the corresponding elements of the other row (column).
  Generally $R_{i} \leftrightarrow R_{i} + kR_{j}$ , $(k \ne 0)$ is used for the addition of $k$ times the $j^{th}$ row to the $i^{th}$ row.
<div style="page-break-after: always;"></div>
# Inverse of a Matrix by Elementary Transformation
**Steps:-**
1. Write $A = IA$
2. Apply suitable elementary row operations to the left hand side of $A=IA$ and also apply the same elementary row transformation to the identity matrix $I$.
3. Keep on apply elementary row transformation till the matrix $A$ reduces to an identity matrix, when this stage comes the original matrix change to $A^{-1}$
## Co-Factor of Matrix
Let's say we have a Square Matrix **A** 
$$
A = \begin{pmatrix}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23}  \\
a_{31} & a_{32} & a_{33}
\end{pmatrix}
$$
**And below is the Co-factor Matrix of A:-**
$$
cof(A) = \begin{pmatrix}
C_{11} & C_{12} & C_{13} \\
C_{21} & C_{22} & C_{23}  \\
C_{31} & C_{32} & C_{33}
\end{pmatrix}
$$
**Also Remember the Sign Conversion:**
$$
cof(A) = \begin{pmatrix}
+ &- & + \\
- & + &- \\
+ &- & + 
\end{pmatrix}
$$
- To find the $C_{11}$, leave the row and column that contain $a_{11}$ and do this $a_{22} a_{33}- a_{32} a_{23} = C_{11}$.
- To find the $C_{21}$, leave the row and column that contain $a_{21}$ and do this $a_{12}a_{33}- a_{32} a_{13} = C_{21}$
- And So on but don't forget to Use the Sign conversion to apply sign of $C_{11} \& C_{21}$.

---
## Adjoint of A Square Matrices
To find the Adjoint first take [[#Co-Factor of Matrix | Co-Factor]] to that matrix and then take [[#Transpose of Matrix]]
$$
adj(A) = \text{(co-factor matrix of A)}^T
$$
---
## Transpose of Matrix
Let *A* be any matrix. Then, $A = [a_{ij}]$ of order $m\times n$.
$$\Rightarrow A^T or A' = [a_{ij}] for 1 \leq i \leq n and 1 \leq j \leq m of order n\times m$$
**Thus $A^T$ is obtained by changing its rows into column and column into rows**