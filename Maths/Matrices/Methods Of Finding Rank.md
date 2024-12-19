---
tags:
  - Maths
  - Matrix
---
To determine the [Rank Of A Matrix](Rank%20Of%20A%20Matrix.md) $A$. We adopt the following different methods:
1. Start with the highest order minor (or minors) of $A$. Let their order by $r$. If any one of them is non-zero, then $\rho(A)=r$.
   
   This method usually involves a lot of computational work since we have to evaluate several determinants.
## Normal Form Method
If $A$ is an $m\times n$ matrix and by a series of elementary (row or column or both) operations, it can be put into one of the following forms (called normal or canonical forms):

$\begin{bmatrix}I_{r}  & \text{O} \\ \text{O} & \text{O} \end{bmatrix},$ $\begin{bmatrix}I_{r} \\ \text{O}\end{bmatrix}$, $\begin{bmatrix}I_{r} & \text{O}\end{bmatrix}$, $\begin{bmatrix}I_{r}\end{bmatrix}$, where $I_{r}$ is the unit matrix of order $r$. 

Since the rank of a matrix is not changed as a result of elementary transformations, it follows that 
$$\rho(A)=r \quad \quad \quad \quad \quad[\because r^{th} \text{ order minor } \mid I_{r }\mid =1 \ne 0]$$

This method is also called **sweep out method or pivotal method.**
###### Procedure to obtain normal form
1. Interchange rows (or columns) to obtain a non-zero element in $\text{I}$ row and $\text{I}$ column of given matrix.
2. Mathis this non-zero element as $1$.
3. Obtain zeros in the the remainder of $\text{I}$ row and $\text{I}$ column.
4. Repeat the above three steps starting with element in $\text{II}$ row and $\text{II}$ column.
5. Continue the process down the main diagonal either until the end of diagonal is reached or all the remaining elements of the matrix is zero.
## Echelon Form Method
In this form of the matrix

   