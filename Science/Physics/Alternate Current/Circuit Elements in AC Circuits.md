#### **(A) A resistor in an ac circuit:-**

If an alternating voltage $V=V_{o}\sin \omega t$ is applied across a resistance, current is $I=I_{o}\sin \omega t$ then using V= IR.
$$
V_{o} = I_{o}R
$$
Thus, it is clear that:
1. The frequency of current in the circuit is $\omega$ and is same as that of applied voltage.
2. In resistance, applied voltage is in phase with the resulting current.

#### **(B) An Inductor in ac circuit**

If a sinusoidal emf $V = V_{o}\sin \omega t$ is applied across an inductor of inductance $L$, then, $$I = I_{o}\sin \left( \omega t-\frac{\pi}{2} \right)$$
With, $$I_{o}=\frac{E_{o}}{\omega t}$$
Thus, it is clear that:
1. The frequency of current in the circuit is same as that of applied emf but current in an inductor 'lags' the applied voltage by $\frac{\pi}{2}$ (or voltage leads the current by $\frac{\pi}{2}$)
2. As here $I_{o}=\frac{E_{o}}{\omega L}$, the quantity $\omega L$ is called "inductive-reactance" and is represented by $X_{L}$ and represents the opposition of a coil to ac, i.e., $$X_{L}=\omega L=2\pi fL$$

#### (C) Capacitor in an ac circuit
If an alternating voltage $V=V_{o}\sin \omega t$ is applied across a capacitor, then, $$I=I_{o}\sin\left(\omega t+\frac{\pi}{2}\right)$$
With, $$I_{o}=V_{o}C\omega$$
Thus, it is clear that:
1. Current in the circuit has same frequency as the applied voltage but leads by $\left( \frac{\pi}{2} \right)$ (or voltage across a capacitor lags the current by $\frac{\pi}{2}$)
2. As here $I_{o}=V_{o}C\omega=\left( \frac{E_{o}}{X_{c}} \right)$ with, $$X_{c}=\frac{1}{\omega C}$$


# Power in AC Circuit 
If an AC voltage $V=V_{o}\sin \omega t$ is applied to a circuit and the resulting current is,
$$
I=I_{o}\sin(\omega t-\phi)
$$
With,
$$
I_{o}=\frac{V_{o}}{Z} \text{ and } \phi=\tan^{-1}\left( \frac{X}{R} \right)
$$
The instantaneous power consumed by the circuit,
$$
P=VI = I_{o}\sin(\omega t-\phi). V_{o}\sin \omega t
$$
So, average power consumed,
$$
P_{av}=\frac{\int _{o}^T P \, dt}{\int _{o}^T \, dt } = \frac{1}{T}V_{o}I_{o}\int _{0}^T \sin \omega t.\sin(\omega t-\phi) \, dt  
$$
$$
\text{Or}
$$
$$
P_{av} = \frac{V_{o}I_{o}}{2T}\int _{o}^T [\cos \phi-\cos(2\omega t-\phi)] \, dt 
$$
Which on simplification with $T=\frac{2\pi}{\omega}$ gives,
$$
P_{av} = \frac{1}{2}V_{o}I_{o}\cos \phi = V_{\text{rms}}I_{\text{rms}}\cos \theta 
$$
Where, $\cos \theta$ is called '**power factor**' of the circuit.



Thus, it is clear that:
1. In case of a '**pure resistance**' as $X=0$ $$PF=\cos \theta=\frac{R}{Z}=\frac{R}{R}=1$$ So, $$P_{av}=V_{\text{rms}}I_{\text{rms}}=\frac{1}{2}V_{o}I_{o}=\text{max}$$
2. In case of a **pure inductance or capacitance** as R = 0, $$PF=\cos \phi = \frac{R}{Z}=\frac{0}{X}=0$$ So, $$P_{av}=V_{\text{rms}}I_{\text{rms}}.0 = 0$$ i.e, average power consumed per cycle in a pure inductance or capacitance is zero, So in an AC circuit if the phase difference between V and I is $\frac{\pi}{2}$. $$ \begin{aligned}i.e., \text{if}\quad V&=V_{o}\sin \omega t \\ I&=I_{o}\cos \omega t\end{aligned}$$ The power consumed by the circuit is zero, such that current is called "**wattless.**"

---
Relation Links:-
- [Alternating Current](Alternating%20Current.md) 
- [Capacitors](../../Capacitors.md) 