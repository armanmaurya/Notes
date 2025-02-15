RF design draws upon many concepts from a variety of fields, including single and systems, electromagnetics and microwave theory, and communications. Nonetheless, RF design has developed its own analytical methods and its own language. For example, while the nonlinear behavior of analog circuits may be characterized by "harmonic distortion", that of RF circuits is quantified by very different measures.
In this we will deals with general concepts that prove essential to the analysis and design of RF circuits, closing the gap with respect to other fields such as analog design, microwave theory, and communications systems. The outline is shown below.
###### Nonlinearity
___
- Harmonic Distortion 
- Compression
- Intermodulation
- Dynamic Nonlinear Systems 

###### Noise
___
- Noise Spectrum
- Device Noise 
- Noise in Circuits 
###### Impedance Transformation 
___
- Series-Parallel Conversion 
- Matching Networks 
- S-parameters
## 1. General Considerations 
#### 1.1 Units in RF Design 
The voltage gain, $V_{out}/V_{in}$, and power gain, $P_{out}/P_{in}$, are expressed in decibels (dB):

```start-multi-column
ID: ID_nt2i
Number of Columns: 2
Largest Column: standard
border:off
```

$$
A_{V}|_{dB} = 20 \log \frac{V_{out}}{V_{in}}
$$


--- column-end ---

$$
A_{P}|_{dB} = 10\log \frac{P_{out}}{P_{in}}
$$

--- end-multi-column

**These two quantities are equal (in dB) only if the input and output voltage appear across *equal* impedances**. For example, an amplifier have an input resistance of $R_{0}$ (e.g., 50 $\Omega$) and driving a load resistance of $R_{0}$ satisfies the following equation:
$$
A_{p}|_{dB} = 10\log\frac{\cfrac{V^2_{out}}{R_{0}}}{\cfrac{V^2_{in}}{R_{0}}}
$$
$$
= 20 \log \frac{V_{out}}{V_{in}}
$$
$$
= A_{v}|_{dB},
$$
Where $V_{out}$ and $V_{in}$ are rms values. In many RF systems, however, this relationship does not hold because the input and output are not equal.
The absolute signal levels are often expressed in dBm rather than in watts or volts. Used for power quantities, **the unit dBm refers to "dB's above 1 mW."** To express the signal power, $P_{sig}$, in dBm, we write 
$$
P_{sig}|_{dBm} = 10\log\left( \frac{P_{sig}}{1 \text{ mW}} \right)
$$
___

###### Example-1  #RF
An amplifier senses a sinusoidal signal and delivers a power of 0 dBm to a load resistance of $50\Omega$. Determine the peak-to-peak voltage swing across the load.
?
**Solution** :
Since 0 dBm is equivalent to 1 mW, for a sinusoidal having a peak-to-peak amplitude of $V_{pp}$ and hence an rms value of $V_{pp}/(2\sqrt{2})$, we write
$$
\frac{V^2_{pp}}{8R_{L}} = 1mW
$$
Where $R_{L} = 50 \Omega$. Thus,
$$
V_{pp} = 632 mV
$$
This is an extremely useful result, as demonstrated in the next example.
___
<!--SR:!2024-01-03,1,230-->

###### Example-2
A GSM receiver senses a narrowband (modulated) single having a level of 100 dBm. If the front-end amplifier provides a voltage gain of 15 dB, calculate the peak-to-peak voltage swing at the output of the amplifier.
?
**Solution**:
Since the amplifier output voltage swing is of interest, we first convert the received signal level to voltage. From the previous example, we note that 100 dBm is 100 dB below 632 $\text{m}V_{pp}$. Also, 100 dB for voltage quantities is equivalent to $10^5$. Thus, 100 dB is equivalent to 6.32 $\mu V_{PP}$. This input level is amplified by 15 dB ($\sim$ 5.62), resulting in an output swing of 35.5 $\mu V_{pp}$.
<!--SR:!2024-01-03,1,230-->

___

The reader may wonder why the output voltage of the amplifier is of interest in the above example. This may occur if the circuit following the amplifier does not present a 50- $\Omega$ input impedance, and hence the power gain and voltage gain are not equal in dB. In fact, the next state may exhibit a purely *capacitive* input impedance, thereby requiring no signal "power.". This situation is more familiar in analog circuits wherein one state drives the gate of the transistor in the next state. As explained in Chapter 5, in most integrated RF system, we prefer voltage quantities to power quantities so as to avoid confusion if the input and output impedances of cascade stage are unequal or contain negligible real parts.
The reader may also wonder why we were able to assume 0 dBm is equivalent to 632 $mV_{pp}$ in the above example even though the signal is not a pure sinusoid. After all, only for a sinusoid can we assume that the rms values is equal to the peak-to-peak value divided by $2\sqrt{ 2 }$. Fortunately, for a narrowband 0-dBm signal, it is still possible to approximate the (average) peak-to-peak swing as 632 mV.
Although dBm is a unit of power, we sometimes use it at interfaces that do not necessarily entail power transfer. For example, consider the case shown in [[Basic Concepts In RF Design#^f52e4e|Fig-1(a)]], where the LNA drives a purely-capacitive load with a 632- $mV_{pp}$ swing, delivering no average power. We mentally attach an ideal voltage buffer to node X and drive a 50 $\Omega$ load (Fig-2(b)). We then say the signal at node *X* has a level of 0 dBm, tacitly meaning that if this signal were applied to a 50 $\Omega$ load, then it would deliver 1 mW.

![[LNA.png#invert|invert | center | 900]] ^f52e4e

#### 1.2 Time Variance
A system is liner if its output can be expressed as a linear combination (superposition) of responses to individual inputs. More specifically, if the outputs in responses to input $x_{1}(t)$ and $x_{2}(t)$ can be respectively expressed as
$$
y_{1}(t) = f[x_{1}(t)]
$$
$$
y_{2}(t) = f[x_{2}(t)]
$$
Then, 
$$
ay_{1}(t) +by_{2}(t) = f[ax_{1}(t) + bx_{2}(t)]
$$
For arbitrary values of *a* and *b*. Any system that does no satisfy this condition is nonlinear. Note that, according to this definition, nonzero initial conditions or dc offsets also make a system nonlinear, but we often relax the rule to accommodate these two effects.
Another attribute of systems that may be confused with nonlinearity is time variance. A system is time-invariant if a time shift is its input results in the same time shift in its output. That is, if $y(t) = f[x(t)]$ then $y(t-τ) = f[x(t-τ)]$ for arbitrary τ.
As an example of an RF circuits in which time variance plays a critical role and must not be confused with nonlinearity, let us consider the simple switching circuit shown in Fig-2(a). The control terminal of the switch is driven by $v_{in1}(t) = A_{1}\cos \omega_{1}t$ and the input terminal by $v_{in_{2}}(t) = A_{2}\cos\omega_{2}t$. We assume the switch is on if $v_{in1} > 0$ and off otherwise. Is this system nonlinearity or time-variant? If, as depicted in Fig-2(b), the input of interest is $v_{in1}$ (while $v_{in2}$ is part of the system and still equal to $A_{2}\cos \omega_{2}t$), then the system is nonlinear because the control is only sensitive to the polarity of $v_{in1}$ and independent of its amplitude. This system is also time-variant because the output depends on $v_{in2}$. For example, if $v_{in1}$ is constant and positive, then $v_{out}(t) = v_{in2}(t)$, and if $v_{in1}$ is constant and negative, then $v_{out}(t) = 0$ (why?).
Now consider the case shown in Fig. 2.2 (c), where the input of interest is $v_{in2}$ (while $v_{in1}$ remains part of system and still equal to $A_{1}\cos \omega_{1}t$). This system is linear with respect to $v_{in1}$. For example, doubling the amplitude of $v_{in2}$ directly doubles that of $v_{out}$. The system is also time-variant due to the effect of $v_{in1}$.

<img style="width: 100px; float: right;" src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/cf/Stepper_motor.jpg/1200px-Stepper_motor.jpg" alt="Your Image">

<p>
  Lorem ipsum dolor sit, amet consectetur adipisicing elit. Alias, autem repudiandae. Magni temporibus voluptas saepe! Et aspernatur autem laborum animi tempora eaque? Fuga molestias rerum optio. Reprehenderit odit dolorem omnis labore accusantium tempore ipsam sapiente provident laboriosam vitae, iure quo ducimus temporibus architecto corrupti autem. Quos dolore expedita molestias dolorum laborum illum odit eius nostrum itaque. Eligendi rem voluptatem veniam consequuntur corrupti aliquam, iusto distinctio magnam in sunt sapiente. Ut ipsa ad praesentium illum recusandae deleniti rem adipisci possimus reprehenderit dolor ex, sequi dignissimos autem provident, quos pariatur iste minima? Autem, aliquam! Deserunt nobis vel nemo inventore cupiditate iusto necessitatibus. Minus, doloribus. Quos rem voluptate inventore deleniti. Eaque amet dolor obcaecati harum officia officiis eius incidunt porro nam ratione quia, deserunt reiciendis deleniti voluptatum nulla minima magnam eveniet, possimus eum ducimus reprehenderit sapiente laboriosam sint. Quis facere quae voluptates sapiente eius in quas eos animi quisquam tempora corrupti hic eveniet maiores tempore nihil perspiciatis, totam rem possimus! Pariatur ducimus recusandae delectus dolorum, sint ut quis consequatur nemo commodi saepe exercitationem alias eius laboriosam rem accusamus consequuntur porro, maiores sed, quidem necessitatibus soluta laudantium voluptatibus sunt quo. Eveniet culpa nulla minus nam quas debitis nobis optio natus dolore. Quisquam voluptatibus nulla voluptatem fuga esse soluta distinctio illo, ut exercitationem officiis sequi id perspiciatis autem consequuntur facere? Dolor numquam quo consequuntur, natus consectetur quod ratione rerum ex tempora, harum error soluta ullam sed sapiente maiores ab mollitia dignissimos animi, adipisci voluptatum officia est. Beatae laboriosam unde ipsum temporibus ullam voluptate eligendi maxime facere explicabo cum. Ipsa minima illum nostrum rerum delectus optio consequatur, nisi ad, mollitia voluptas officia magnam tenetur quod eos laudantium possimus, nesciunt architecto quaerat culpa vel ipsam eveniet! Assumenda molestias sunt ratione nulla vel enim quis accusamus quos neque, illo incidunt optio mollitia expedita! Doloremque, inventore. Omnis, sequi! Expedita.

</p>



