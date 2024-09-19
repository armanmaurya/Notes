---
tags:
  - Rotation
---
# Moment of Inertia
The measures of the property by virtue of which a body revolving about an axis opposes any change in rotational motion is know as moment of inertia.

MOI of Point Mass separated by distance $r$ is given by:
$$
MoI = mr^2
$$
Where:
- $m$ is the mass of body
- $r$ is the perpendicular distance from axis of Rotation.

**Unit:** SI : $kg-m^2$, CGS : $g-cm^2$
**Dimensions:** $[M^1L^2T^0]$

# Calculation of MOI
---
There are two types of system in which we can calculate moment of inertia are :
1. Discrete Mass bodies
2. Continuous Mass bodies 

### 1. Discrete Mass Bodies 
The system of point masses (No dimensions of itself), to calculate MOI for total system the formula is given as,
$$
I = \Sigma_{i=1}^{i=n} \ m_{i}r_{i}^2
$$
Calculate the MOI of individual point masses then, Sum MOI of all individual point masses
### 2. Continuous Mass Bodies 
The system where mass is distributed (Disc, Rod, Ring, Cylinder), to calculate MOI for this system the formula is given as,
$$
I = \int dm \ r^2 
$$
*Where::* $dm$ is Mass of Element.

$$
1D: dm = \lambda dx, \quad 2D: dm = \sigma dA, \quad 3D = \rho dV
$$

If $\lambda, \sigma, \rho$ is constant (Uniform Mass density) then, value of $\lambda, \sigma, \rho$ will be,
$$
\lambda = \frac{M}{L},\quad \sigma = \frac{M}{A}, \quad \rho = \frac{M}{V}
$$
# Theorems of MOI
There are basically two theorems from which we can calculate MOI of any body
1. [Perpendicular Axis Theorem](Perpendicular%20Axis%20Theorem.md)
2. [Parallel Axis Theorem](Parallel%20Axis%20Theorem.md)

# Links 
---
1. [Radius of Gyration](Radius%20of%20Gyration.md) 