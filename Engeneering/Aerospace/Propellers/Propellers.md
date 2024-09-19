# Propellers

A propeller, like an airplane wing, is an [Aerofoils](Aerofoils.md). When air moves over the surface of a moving propeller on an airplane, the air pressure in front of the propeller is reduced or velocity of air in front of propeller is increased, and the air pressure behind the propeller increased or velocity of air behind the propeller is decreased. The pressure imbalance tends to push the airplane forward. We say that the propeller is generating ***thrust***.

The same principle applies to helicopter propellers, only now the propeller rotates around the vertical axis. The pressure on top of the propeller is reduced hence, velocity of air increased and the pressure underneath is increased hence, velocity of air decreased, generating ***lift***.
![center](images/Aero_img032.gif)

The illustration defines some terms that are used to describe the shape of propeller. The radius (r) of the propeller is the distance from the center to the tip. The chord length (c) is the straight-line width of the propeller at a given distance along the radius. Depending on the design of the propeller, the chord length may be constant along the entire radius, or it may vary along the radius of the propeller. Another variable is the twist angle $(\beta)$ of the propeller, which may also very along the radius of the propeller.

# Pitch

---

The displacement a propeller makes in a complete spin of $360\degree$ degrees. This means that if we have a propeller of pitch 40 is will advance 40 inches for every complete spin as long as this is made is a solid surface; in a liquid environment, the propeller will obviously slide with less displacement.

The pitch concept is not exclusive for propellers, other mechanical devices like screws also use it. For instance, a screw with 10 mm of pitch will advance 10 mm for every complete turn when hit by the screwdriver. In fact, the "screw propeller" concept is literally making reference to that the propeller works exactly like a screw.
![center](images/tnl502.jpg)
It is very important that both, pitch and diameter, are properly calculated. If for any given HP (Horse-Power) the pitch is too big, the propeller becomes heavy and demands more power than the engine can reach and vice versa, If the pitch is too small then we have a light propeller that wouldn't absorb the engine's full power.

![](images/Definition-of-propeller-pitch%201.png)

## Efficiency

The efficiency of a propeller is determined by,

- Thrust coefficient $$c_{T} = \frac{T}{\rho.n^2.D^4}$$
- torque coefficient $$c_{Q}=\frac{Q}{\rho.n^2.D^5}$$
- propeller power coefficient. $$c_{P}=\frac{P}{\rho.n^2.D^5}$$

Where, 

- $\rho$ is air density
- $n$ is propeller rotational speed 
- $D$ is propeller diameter

# Thrust

Propeller thrust is dependent on the properties of the propeller and air around it. Equation can be expressed in a two different ways.

- Static thrust
- Dynamic thrust 

#### Static thrust

Thrust is dependent on the mass flow rate of the air and the change in air velocity: 

$$
F_{\text{thrust}}=m \times [V_{e}-V_{o}]
$$

Where,

- $m$ = mass flow rate
- $V_{e}$ = exit velocity of air
- $V_{o}$ entrance velocity of air

The mass flow rate can be expressed as,
$$m=\rho \times V_{p} \times A$$
Where,

- $\rho$ is the air density
- $A$ is the cross-sectional area of the propeller.
- $V_{p}$ is the incoming air velocity.

---

# Links

- [Aerofoils](Aerofoils.md) 
- [Blade Angle](Blade%20Angle.md) 
