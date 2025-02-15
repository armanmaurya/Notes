---
aliases:
  - DC Motor
  - Motors
Branch: Electrical
Topic: DC Motors
tags:
  - Motor
---
A DC motor is an electrical machines that converts electrical energy into mechanical energy. In a DC motor, the input electrical energy is the direct current which is transformed into the mechanical rotation.

Therefore, there are three general types of dc motors are:-
- Self Excited DC Motor
	- Shunt motor
	- Series motor
	- Compound motor. 
	- The permanent-magnet (PM) motor is special case of a shunt motor with uniform flux density.
- Separately Excited DC Motor

The principle of operation of a dc motor is explained in detail in Section 3.4. A brief review is given here. In a dc motor, a uniform magnetic field is created by its poles. The armature conductors are forced to carry current by connecting them to a dc motor source(supply) as shown in  Figure-1. The current direction in the conductors under each pole is kept the same by the commutator. According to the Lorentz force equation, **a current-carrying conductor when placed in a magnetic field experience a force that tends to move it.** This is essentially the principle of operation of a dc motor. All the conductors placed on the periphery of a dc motor are subjected to these forces, as shown in figure. These forces cause the armature to rotate in the clockwise direction. Therefore, **the armature of a dc motor rotates in the direction of the torque developed by the motor.** For this reason, the torque developed by the motor is called the **driving torque.** Note that the torque developed by the conductors placed on the armature of a dc generator is in a direction opposite to its motion. Therefore, it can be labeled the **retarding torque.**
The magnitude of the average torque developed by these forces must be the same in both machine, since it does not matter whether the current is forced through the armature conductors by an external power source or is the result of induced emf in the conductors. Thus,
$$T_{d} = K_{a}\Phi_{p}I_{a}$$

![[../../../Jee/Maths/Conic Section/Images/Untitled.png]] 

Where $K_a = PZ/2\pi$ a is the machine constant, $\Phi_p$ is the flux per pole, and $I_a$ is the armature current.
As the armature rotates, each coil on the armature experiences a change in the flux passing through its plane. Therefore, an electromotive force (emf) is induced in each coil. In accordance with Faraday’s law of induction, the induced emf must **oppose** the current entering the armature. In other words, the induced emf opposes the applied voltage. For this reason, we commonly refer to the induced emf in a motor as the **back emf** or **counter emf** of the motor.

The average value of the induced emf at the armature terminals should, however be the same as that for a dc generator because it does not really matter whether the armature is being driven by a prime mover or by its own driving torque. Thus,
$$E_a = K_a\Phi_p\omega_m$$
where $\omega_m$ is the angular velocity of the armature (rad/s).
If $R$ is the effective (total) resistance in the armature circuit and $V_s$ is the applied voltage across the armature terminals, then the armature current is
$$I_a = \frac{V_s - E_a}{R}$$
Since the resistance of the armature circuit $R$ is usually very small, the voltage drop across it is also small in comparison with the back emf $E_a$. Therefore, most of the applied voltage $V_s$ is needed to over the back emf $E_a$. It should also be evident from the above equation that the back emf in the motor is smaller than the applied voltage.

### 1.1 Starting a DC motor
At the time of starting, the back emf in the motor is zero because the armature is not rotating. For a small value of the armature-circuit resistance $R$, the starting current in the armature will be extremely high if the rated value of $V_s$ is impressed across the armature terminals. The excessive current can cause permanent damage to the armature windings. Thus, a dc motor never be started at its rated voltage. In order to start dc motor, an external resistance must be added in series with the same armature circuit, as shown in Figure-2 for PM motor. The external resistance is gradually decreased as the armature comes up to speed. Finally, when the armature has attained its normal speed, the external resistance is “cut out” of the armature circuit.
### 1.2 Armature Reaction
The theory of commutation and armature reaction as outlined in Direct Current Generator for dc generators is also applicable to dc motors. The only difference is that the direction of the current in a conductor under a pole in a dc motor is opposite to that in a generator for the same direction of rotation. Therefore, the field created by the current in the armature of dc generator. Since the brushes should be retreated in a dc motor.

If a dc machine has interpoles, the polarities of the interpoles for the dc motor must be opposite to those of the dc generator. As the interpoles carry armature current and the armature current is already in the opposite direction, the interpole polarities are automatically reversed. The same is true for the compensating windings. Therefore, no action is needed when a dc generator designed with interpoles or compensating windings is used as a dc motor.

## 2. Speed Regulation
**The armature current of a motor increases with load**. For a constant applied voltage, the increase in the armature current result in a decrease in the back emf. **The reduction in the back emf causes a drop in the speed of the motor**. The speed regulation is a measure of the change in speed from no load to full load. When the change in speed at full load is expressed as a percent of its full-load speed, it is called the percent speed regulation(SR%). In equation form, the percent speed regulation is
$$SR\% = \frac{N_{mnL} - N_{mfL}}{N_{mfL}} \times 100 = \frac{\omega_{mnL} - \omega_{mfL}}{\omega_{mfL}} \times 100$$

Where $N_{mnL}$ ($\omega_{mnL}$) is the no-load speed, and $N_{mfL}$($\omega_{mfL}$) is the full-load speed of a dc motor.

As we continue out discussion of dc motor, we will observe that (a) a series motor is a variable-speed motor because its speed regulation is very high, (b) a shunt motor is essentially a constant-speed motor because its speed regulation is very small, and (c) a compound motor is a variable-speed motor because its speed regulation is higher that that of the shunt motor.

## 3. Losses in a DC Motor
The power input to a dc motor is electrical and the power output is mechanical. The difference between the power input and the power output is the power loss. A dc motor portrays the same power losses as a dc generator. ( For details, refer to Section 5.11.)
When the power is supplied to a motor, a significant portion of that power is dissipated by the resistances of the armature and the field windings as copper loss. The armature by the resistances of the armature and the field windings as copper loss. The remainder power ( the developed power ) is converted by the motor into mechanical power. A part of the developed power is consumed by the rotational loss. The difference is the net mechanical power available at the shaft of the motor.
A typical power-flow diagram of a dc motor is shown in Figure-3.
## 4. A Series Motor
In a series motor the field winding is connected in series with the armature circuit as shown in Figure-4. We have also included an external resistance $R_{ax}$ in series with the armature that can be used either to start the motor and then be shorted or to control the speed of the motor. Since the series field winding carries the rated armature current of the motor, its has few turns of heavy wire. As the armature current changes with the load, so does the flux produced by the field winding. In other words, the flux set up by a series motor is function of the armature current. If the flux per pole can be expressed as
$$\Phi_{p} = k_{f}I_{a}$$
then the back emf is
$$E_{a}=K_{a}k_{f}I_{a}\omega_{m}$$
and the torque developed by the series motor is
$$
T_{d}K_{a}k_{f}I_{a}^2
$$

^9278ef

From the above equations, it is evident that the back emf in the motor is proportional to the armature current, and the torque developed by a series motor is proportional to the **square** of the the armature current as long as the motor is operating in the linear region. As the armature current increases, so does the flux produced by it. An increase in the flux enhances the level of saturation in the motor. When the motor is saturated, the flux increases only gradually with further increase in the armature current. Hence, the torque developed in no longer proportional to the square of the current. Hence, the torque developed is no longer proportional to the square of the current. The torque versus armature current characteristic of a series motor is given in Figure-5.
When a series motor operates under no load, the torque developed by the motor is just sufficient to overcome the rotational loss in the machine. Since the rotational loss is only a fractional of the full-load torque, the torque developed by the machine is very small. Therefore, the back emf at no load must be the armature current and the armature current is a small fractional of its rated value, the motor must attain a relatively high speed. In fact, it is possible for a series motor to self-distrust under no load owing to centrifugal action.
As we load the motor, the torque developed by it must increase. The increase in the torque necessitates an increase in the armature current. The increase in the  torque necessitates an increase in the armature current. The increase in the armature current causes an increase in the voltage drop across the armature-current resistance, the field-winding resistance, and the external resistance. For a fixed applied voltage, the back emf must decrease with load. Since the back emf is also proportional to the armature current, the speed of the motor must drop. Figure-6 shows the torque-speed characteristic of a series motor. We will comment on by a series motor as a function of its speed.
From the equivalent circuit of Figure-4, we have  ^43baa3
$$\begin{aligned}
E_{a} &= V_{s}I_{a}(R_{a} +R_{s} + R_{ax}) \\
&= V_{s}-I_{a}R
\end{aligned}$$
Where $R = R_{a} +R_{s} +R_{ax}$ is the total armature-circuit resistance. Substituting for $E_{a}$ from Eq. (6.7), we can obtain an expression for the speed of the motor in terms of armature current as
$$
\omega_{m} = \frac{V_{s} - I_{a}R}{K_{a}k_{f}I_{a}}
$$

^052161

This equation states that the speed of a series motor is practically inversely proportional to the armature current. The nature of the speed-current characteristic is depicted in Figure-5.
[[Direct Current Motors#^052161|Equation-9]]  can also be rewritten as
$$
I_{a} = \frac{V_{s}}{K_{a}k_{f}\omega_{m} +R}
$$

The torque developed, from [[Direct Current Motors#^9278ef|Eq. (6.8)]] , can now be expressed as 
$$
T_{d} = \frac{K_{a}k_{f}V_{s}^2}{[R +K_{a}k_{f}\omega_{m}]^2}
$$
From this equation it is evident that for all practical purpose, the torque developed by a series motor is inversely proportional to the square of its speed. The nature of the speed-torque characteristic in Figure-6 should now be obvious. A series motor provides high torque at low speed and low torque at high speed. For this reason, a series motor is suitable for hoists, cranes, electric trains, and a host of other applications that require large starting torques.
Since the torque developed by a series motor  is also proportional to the square of the applied voltage, the torque developed by it can be controlled by controlling the applied voltage. For example, at given speed, doubling the applied voltage results in quadrupling of the torque. 
The power developed by a series motor is 
$$
\begin{aligned}
P_{d} &= E_{a}I_{a} \\
&= [V_{s} - I_{a}R]I_{a}
\end{aligned}
$$ 
The power developed by a series motor for a constant applied voltage is maximum when $I_{a} \rightarrow I_{am}$ and $\frac{dP_{d}}{dI_{a}} \rightarrow 0$. Thus, differentiating the above equation with respect to $I_{a}$ and setting it to zero, we obtain
$$
I_{am} = \frac{V_{s}}{2R}
$$
The maximum power developed by a series motor is 
$$
P_{dm} = \frac{V^2_{s}}{4R}
$$
For a stable operation, the operating range of a series motor is well below the maximum power developed by it. The power (and the torque developed) as a function of armature current are shown in Figure-5.
___

##### **Example-1** #Motor
The magnetization curve of 10-hp, 220V series motor is given in Figure 6.7 at 1200 rpm. The other parameters of the series motor are $R_{a} = 0.75\Omega, R_{s} = 0.25\Omega$, and $P_{r} = 1.04 kW$. What is the armature current when the motor delivers its rated load at 1200 rpm? What the load is gradually reduced, the armature current decrease to 16.67 A. Determine (a) the new speed of the motor and (b) the driving torque.
?
⦿ **Solution**
$$
\begin{aligned}
\text{The Power output} &: P_{o} = 10 \times 756 = 7460\ W \\
\text{The Power developed} &: P_{d} = P_{o} + P_{r} = 7460 + 1040 = 8500 \ W \\
\text{The armature-circuit resistance} &: R = 0.25 + 0.75 = 1\Omega
\end{aligned}
$$
Since,
$$
P_{d} = E_{a}I_{a} = 8500W \text{ and } E_{a} = V_{s} - I_{a}R,
$$
We have,
$$
E_{a}I_{a} = [V_{s}-I_{a}R]I_{a}
$$
Substituting the value, we obtain
$$I_{a}^2 - 220I_{a} + 8500 = 0$$
$$
or
$$
$$
I_{a} = 50A
$$
The power input: $P_{in} = V_{s}I_{a} = 220 \times 50 = 11,000W$
Hence,
$$
\eta = \frac{7460}{11,000} = 0.6782 \quad or \quad 67.82\%
$$
The induced emf: $E_{a} = 220 -50 \times 1 = 170V$
From the magnetization curve at 1200 rpm, the magnetomotive force (mmf) of the series field winding corresponding to a back emf of 170 V is 150 A.t/pole.
Hence, the turns per pole are
$$
N_{s} = \frac{150}{50} = 3 \text{ turns/pole}
$$
At the reduced load: $I_{am} = 16.67 A$
$$
E_{an} = 220 - 16.67 \times 1 = 203.33V
$$
The mmf of the series winding is $16.67 \times 3 = 50 \text{ A.t/pole.}$ From the magnetization curve , the back emf at 1200 rpm is 90 V. In order to obtain a back emf of 203.33 V at the same mmf of 50 A.t/pole, the new speed of the motor is
$$
N_{mn} = \frac{203.33}{90} \times 1200 \sim 2711 rpm or \omega_{mn} = 283.9 \text{rad/s}
$$
The power developed at reduced load: $P_{dn} = 203.33 \times 16.67 = 3389.51 W$
$$
T_{dn} = \frac{3389.51}{283.9} = 11.94 \text{ N.m}
$$
<!--SR:!2024-01-03,1,226-->

___
## 5. Stunt Motor 
The equivalent circuit of a shunt motor is shown in Figure 6.8 with a starting resistor in the armature circuit. The field winding is connected directly across the source. For a constant-source voltage, the flux created by the field winding is constant. The torque developed by the motor is 
$$
T_{d} = K_{a}\Phi_{p}I_{a} = KI_{a}
$$

^5ca669

Where $K = K_{a}\Phi_{p}$ is a constant quantity. Hence the torque developed by a shunt motor is proportional to the armature current as shown in Figure-9.
When the shunt motor is driving a certain load, the back emf of the motor is 
$$
E_{a} = V_{s}-I_{a}R_{a}
$$
Since $E_{a} = K_{a}\Phi_{p}\omega_{m},$ the operating angular velocity (speed) of the motor is
$$
\omega_{m} = V_{s}-\frac{I_{a}R_{a}}{K_{a}\Phi_{p}}
$$

^fb1072

Although we are developing relationship in terms of the angular velocity $\omega_{m}$, we still refer to it as the speed of the motor.
When the load on the motor is increased, the following sequence of events takes place: 
1. The armature current $I_{a}$ increases to satisfy the demand of increased load.
2. The voltage drop across the armature circuit resistance is $R_{a}$ increases. 
3. For a fixed-source voltage, the back emf $E_{a}$ decreases.
4. Since The flux is constant when armature reaction is negligible, the decrease in the back emf of the motor is accompanied by a decrease in its speed as shown in Figure-10 (*curve d*).

With the increase in the armature current, the armature reaction becomes more significant if the motor is not compensated for it. The increase in the armature reaction decreases the flux in the motor, which, in turn, causes an increase in the speed. Depending upon the magnetic saturation of the motor and the severity of the armature reaction, the increase in the speed due to the armature reaction may be less than, equal to, or greater than the drop in the speed due to the increase in the armature current, as depicted in Figure-10 by curves *a, b,* and *c*, respectively. Curve *c* is not really desirable, as it may lead to instability of operation. We can overcome this undesirable effect by adding few series turns in the motor. Such a winding, when included as a part of a shunt motor, is called the stabilizing winding.
[[Direct Current Motors#^fb1072|Equation-16]] can also be written as 
$$
\omega_{m} = \omega_{mnL} - \frac{R_{a}}{K_{a}\Phi_{p}}I_{a}
$$
Where $\omega_{mnL}$ = $V_{s}/K_{a}\Phi_{p}$ is the no-load speed of the motor. This is the speed at which the torque developed by the motor is zero. The actual speed of the motor is bound to be lower than $\omega_{mnL}$. In other words, a shunt motor is basically a constant-speed motor.
We can also obtain an expression for the torque developed in terms of the speed of the motor from [[Direct Current Motors#^5ca669|Eq-14]] and [[Direct Current Motors#^fb1072|Eq-16]] as 
$$
T_{d} = \frac{K_{a}\Phi_{p}V_{s}}{R_{a}} - \frac{K_{a}^2\Phi_{p}^1}{R_{a}}\omega_{m}
$$
This straight-line relationship, depicted in Figure-11, is the torque-speed characteristic of a shunt motor. It simply states that the speed increases as the load on the motor decreases. Also plotted in Figure-11 is the power developed by the machine as a function of its speed. We can show that the power developed by a shunt motor is maximum when its speed is equal to $0.5\omega_{m}$. The corresponding expression for the maximum power developed by the machine is
$$
P_{dm} = \frac{V^2_{s}}{4R_{a}}
$$
___

##### Example-2 #Motor 
A 240 V shunt motor takes a current of 3.5 A on no load. The armature circuit resistance is $0.5\Omega$ and the shunt field winding resistance is $160\Omega$. When the motor operates at full load at 2400 rpm, it takes 24 A. Determine (a) its efficiency at full load, (b) torque developed and the useful torque, (c) the no-load speed, and (d) percent speed regulation. Sketch the power-flow diagram for each operating condition.
?
⦿ **Solution**
**No-load condition:**
	Shunt-field current:     $I_{fnL} = \frac{240}{160} = 1.5A$
	Armature current: $I_{anL} = 3.5 - 1.5 = 2A$
	The back emf: $E_{anL} = 240 -2 \times 0.4 = 239.2V$
	Power developed: $P_{dnL} = 239.2 \times 2 = 478.4 W$
	Total copper loss: $P_{cunL} = 2^2 \times 0.4 + 240 \times 1.5 = 361.6W$
	Power input: $P_{innL} = 240 \times 3.5 = 840W$
	At no load, the rotational loss must be equal to the power developed because the power output is zero as shown in Figure-12 a. We also assume that the rotational loss remains constant under all load condition. Thus, $P_{r} = 478.4W$
**Full-load condition**
	Power input: 

___

___

## The Compound Motor 
A shunt motor may have an additional series field winding in the same manner as a shunt generator. The series field winding may be connected so that the flux produced by it aids the flux set up by the shunt field winding, in which case the motor is said to be a **cumulative compound motor.** A motor is said to be **differential compound** when the flux of the series field winding opposes the flux of the shunt field winding. In fact, the stabilizing winding discussed in the previous section makes a shunt motor to behave like a cumulative compound motor.
A compound motor may be connected either as a **short-shunt motor** or a **long-shunt motor**. In a long shunt field winding is directly connected across the power source as depicted in Figure-13b. Therefore, the flux created by the shunt field winding is constant under all loading conditions. On the other hand, the shunt field winding of a short-shunt compound motor is connected directly across the armature terminals as shown in Figure-13a. The flux created by the shunt field winding of a short-shunt motor decreases (somewhat) with an increase in the load owing to the voltage drop across the series field winding.
As you may have guessed, the characteristic of a compound motor are a 

---
Related Links:-
- [Torque On Current Carrying Loop In Magnetic Field](../../../Jee/Torque%20On%20Current%20Carrying%20Loop%20In%20Magnetic%20Field.md) 