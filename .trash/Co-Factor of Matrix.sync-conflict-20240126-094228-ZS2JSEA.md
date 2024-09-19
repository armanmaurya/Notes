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
Related Links:-
- [Adjoint Of A Square Matrices](Adjoint%20Of%20A%20Square%20Matrices.md) 
