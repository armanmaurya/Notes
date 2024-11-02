**Euclidean Distance** gives the distance between any two points in an n-dimensional plane. Euclidean distance between two points in the Euclidean space is defined as the length of the line segment joining the two points.

Euclidean distance is like **measuring the straightest and shortest path between two points**. This **metric is based on the Pythagorean theorem** and is widely utilized in various fields such as machine learning, data analysis, computer vision, and more.
## Formula
##### In 2D
Consider two points (x1, y1) and (x2, y2) in a 2-dimensional space; the Euclidean Distance between them is given by using the formula:
$$
d = \sqrt{ [(x_{2}-x_{1})^2+ (y_{2}- y_{1})^2] }
$$
**Where:**
- $d$ is Euclidean Distance
- $(x_{1},y_{1})$ is Coordinate of the first point
- $(x_{2},y_{2})$ is Coordinate of the second point 
##### In 3D
If the two points (x1, y1, z1) and (x2, y2, z2) are in a 3-dimensional space, the Euclidean Distance between them is given by using the formula:
$$
d = \sqrt{ [(x_{2}-x_{1})^2 +(y_{2}- y_{1})^2+(z_{2}-z_{1})^2] }
$$
**Where:**
- $d$ is Euclidean Distance
- $(x_{1},y_{1},z_{1})$ is Coordinate of the first point
- $(x_{2},y_{2}, z_{2})$ is Coordinate of the second point 
##### In nD
In general, the Euclidean Distance formula between two points $(x_{11},x_{12}, x_{13},\dots, x_{1n})$ and $(x_{21}, x_{22}, x_{23},\dots, x_{2n})$ in an n-dimensional space is given by the formula:
$$
d=\sqrt{ \left[ \sum_{i=1}^n(x_{2i}-x_{1i})^2 \right] }
$$
**Where**
- $i$ Ranges form 1 to n
- $d$ is Euclidean distance
- $(x_{11}, x_{12}, x_{13},\dots, x_{1n})$ is Coordinate of First Point
- $(x_{21}, x_{22}, x_{23},\dots, x_{2n})$ is Coordinate of Second Point

---
**References**
- https://www.geeksforgeeks.org/euclidean-distance/