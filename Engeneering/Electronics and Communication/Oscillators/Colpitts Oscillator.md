Colpitts Oscillator is the exact opposite of the Hartley Oscillator. Just like the Hartley Oscillator, the tuned tank circuit consists of an LC resonance sub-circuits connected between the collector and the base of a single stage transistor amplified producing a sinusoidal output waveform. 

The basic configuration of **Colpitts Oscillator** resembles that of the Hartley Oscillator but the difference this time is that the centre tapping of the tank sub-circuit is now make at the junction of a "Capacitive voltage divider" network instead of a tapped autotransformer type inductor as in Hartley oscillator.
![center](images/oscillator-osc42.gif)

The Colpitts oscillator uses a capacitive voltage divider network as its feedback source. The two capacitors, $C_{2}$ and $C_{2}$ are placed across a single common inductor, L as shown. Then $C_{1}$, $C_{2}$ and L form the tuned tank circuit with the condition for oscillations being: $X_{C1}$ + $X_{C2}$ = $X_{L}$, the same as for the Hartley oscillator circuit.

The advantage of this type of capacitive circuit configuration is that with less self and mutual inductance within the tank circuit, frequency stability of the oscillator is improved along with a more simple design.

As with the Hartley oscillator, the Colpitts oscillator uses a single stage bipolar transistor amplifier as the gain element which produces a sinusoidal output. Consider the circuit below.

 **Basic Cricut:-**

---
![center](images/oscillator-osc13.gif)
The emitter terminal of the transistor is effectively connected to the junction of the two capacitors, C1 and C2 which are connected in series and act as a simple voltage divider. When the power supply is firstly applied, capacitors C1 and C2 charge up and then discharge through the coil L. The oscillations across the capacitors are applied to the base-emitter junction and appear in the amplified at the collector output.

Resistors, R1 and R2 provide the usual stabilizing DC bias for the transistor in the normal manner while the additional capacitors act as a DC-blocking bypass capacitors. A radio-frequency choke (RFC) is used in the collector circuit to provide a high reactance (ideally open circuit) at the frequency of oscillation, ( ƒr ) and a low resistance at DC to help start the oscillations.

The required external phase shift is obtained in a similar manner to that in the Hartley oscillator circuit with the required positive feedback obtained for sustained undamped oscillations. The amount of feedback is determined by the ratio of C1 and C2. These two capacitances are generally “ganged” together to provide a constant amount of feedback so that as one is adjusted the other automatically follows.

The frequency of oscillations for a Colpitts oscillator is determined by the resonant frequency of the LC tank circuit and is given as: 
$$f_{r} = \frac{1}{2\pi \sqrt{ LC_{T} }}$$
Where, $C_{T}$ is the capacitance of $C_{1}$ and $C_{2}$ connected in series and is given as:
$$
\frac{1}{C_{t}}=\frac{1}{C_{1}}+\frac{1}{C_{2}} \quad \text{or} \quad C_{T} = \frac{C_{1}\times C_{2}}{C_{1}+C_{2}}
$$
The configuration of the transistor amplifier is of a _Common Emitter Amplifier_ with the output signal 180o out of phase with regards to the input signal. The additional 180o phase shift require for oscillation is achieved by the fact that the two capacitors are connected together in series but in parallel with the inductive coil resulting in overall phase shift of the circuit being zero or 360o.

The amount of feedback depends on the values of C1 and C2. We can see that the voltage across C1 is the the same as the oscillators output voltage, Vout and that the voltage across C2 is the oscillators feedback voltage. Then the voltage across C1 will be much greater than that across C2.

Therefore, by changing the values of capacitors, C1 and C2 we can adjust the amount of feedback voltage returned to the tank circuit. However, large amounts of feedback may cause the output sine wave to become distorted, while small amounts of feedback may not allow the circuit to oscillate.

Then the amount of feedback developed by the Colpitts oscillator is based on the capacitance ratio of C1 and C2 and is what governs the the excitation of the oscillator. This ratio is called the “feedback fraction” and is given simply as:
$$
\text{Feedback Fraction} = \frac{C_{1}}{C_{2}}\%
$$

**Examples:-**

---

>[!example]- Example-1 
>A **Colpitts Oscillator** circuit having two capacitors of 24 nF and 240 nF respectively are connected in parallel with an inductor of 10 mH. Determine the frequency of oscillations of the circuit, the feedback fraction and draw the circuit.
>**Solution**
>The oscillation frequency for a Colpitts Oscillator is given as:
> $$f_{r} = \frac{1}{2\pi \sqrt{ LC_{T} }}$$
>As the colpitts circuit consists of two capacitors in series, the total capacitance is therefore:
> $$
>C_{T} = \frac{24\text{nF} \times 240\text{nF}}{24\text{nF}+ 240\text{nF}}= 21.82\text{nF}
>$$
>The inductance of the inductor is given as 10 mH, then the frequency of oscillation is:
> $$ f_{r} = \frac{1}{2\pi \sqrt{ LC_{T} }}= \frac{1}{6.283\sqrt{ 0.01 \times 21.82 \times 10^{-9} }} = 10.8 \text{kHz}$$
>The frequency of oscillations for the Colpitts Oscillator is therefore 10.8 kHz with the feedback fraction given as:
> $$
>F_{F} = \frac{C_{1}}{C_{2}}= \frac{24\text{nF}}{240\text{nF} = 10\%}
>$$

**Summary:-** 

---
Then to summarise, the **Colpitts Oscillator** consists of a parallel LC resonator tank circuit whose feedback is achieved by way of a capacitive divider. Like most oscillator circuits, the Colpitts oscillator exists in several forms, with the most common form being similar to the transistor circuit above.

The centre tapping of the tank sub-circuit is made at the junction of a “capacitive voltage divider” network to feed a fraction of the output signal back to the emitter of the transistor. The two capacitors in series produce a 180o phase shift which is inverted by another 180o to produce the required positive feedback. The oscillating frequency which is a purer sine-wave voltage is determined by the resonance frequency of the tank circuit.

In the next tutorial about Oscillators, we will look at RC Oscillators which uses resistors and capacitors as its tank circuit to produce a sinusoidal waveform.

---
- [LC Oscillator](../../../Jee/LC%20Oscillator.md) 