---
tags:
  - numpy
  - python
---
Write a NumPy program to compute the outer product of two given vectors.
**NumPy: Outer product of two vectors**

**Solution:**
**Python Code:**
```python
import numpy as np

# Define two 2x2 matrices 'p' and 'q'
p = [[1, 0], [0, 1]]
q = [[1, 2], [3, 4]]

# Display the original matrices 'p' and 'q'
print("Original matrices:")
print(p)
print(q)

# Compute the outer product of matrices 'p' and 'q' using np.outer
result = np.outer(p, q)

# Display the outer product of the matrices
print("Outer product of the said two vectors:")
print(result)
```
```
original matrix:
[[1, 0], [0, 1]]
[[1, 2], [3, 4]]
Outer product of the said two vectors:
[[1 2 3 4]
 [0 0 0 0]
 [0 0 0 0]
 [1 2 3 4]]
```
**Explanation:**

> [!note] Title
> $P = [[1, 0], [0, 1]]$
> $Q = [[1, 2], [3, 4]]$ 
> At first two $2 \times 2$ matrixes P and Q have been declared.
> 
> `result = np.outer(p, q)`
> This line calculates the outer product of p and q. The outer product is calculated by taking the Cartesian product of the elements in p and q, and multiplying them together.
> `np.outer` flattens `p = [1, 0, 0, 1]` and `q = [1, 2, 3, 4]`.
> 
> ```
>[[1*1, 1*2, 1*3, 1*4],
>[0*1, 0*2, 0*3, 0*4],
>[0*1, 0*2, 0*3, 0*4],
>[1*1, 1*2, 1*3, 1*4]]
> ```

Finally print() prints the resulting 4x4 matrix.

---
**Related Links**
- [Matrices](../../../Science/Maths/Matrices/Matrices.md)

