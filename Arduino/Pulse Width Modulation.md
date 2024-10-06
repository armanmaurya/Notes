PWM allows you to simulate analog output by rapidly switching between on and off states. The percentage of time the signal is high (the duty cycle) determines the average voltage sent to a device, such as an LED or a motor.
- **[Arduino](Arduino.md) PWM pins** (3, 5, 6, 9, 10, 11) output a 5V signal.
- You can change the average voltage by adjusting the duty cycle between 0 (0% duty cycle, 0V) and 255 (100% duty cycle, 5V).
- To achieve 3.3V (instead of 5V), you need to limit the duty cycle to a value that corresponds to 3.3V.
### **Calculating the Duty Cycle for 3.3V:**
To calculate the duty cycle corresponding to 3.3V when using a 5V PWM signal, you use the following formula:
$$
\text{Duty Cycle} = \left(\frac{\text{V}_{\text{desired}}}{\text{V}_{\text{max}}}\right)\times 255
$$
Where:

- $V_{\text{desired}}$ =3.3V
- $\text{V}_{\text{max}}$ = 5V (the Arduino output voltage)
- 255 is the maximum PWM value (100% duty cycle).

## Calculation
$$
\text{Duty Cycle} = \left( \frac{3.3}{5} \right)\times 255 \sim 168
$$
So, the maximum duty cycle for 3.3 V is 168 (out of 255).
## Arduino Code Example
The following code will cycle the PWM signal from 0V to 3.3V by adjusting the duty cycle from 0 to 168 and back to 0:
```cpp
int pwmPin = 9;   // Pin 9 supports PWM output
int dutyCycle = 51;  // Corresponds to ~1V output

void setup() {
  pinMode(pwmPin, OUTPUT);  // Set pin 9 as an output
}

void loop() {
  analogWrite(pwmPin, dutyCycle);  // Output PWM signal with ~1V average voltage
}
```
### **How It Works:**
- **analogWrite(pwmPin, dutyCycle)**: Sends a PWM signal to the specified pin, where `dutyCycle` is a value between 0 (0V) and 168 (~3.3V).
- **Loop**: The code first increases the duty cycle from 0 to 168, making the voltage rise from 0V to 3.3V, then it decreases the duty cycle back to 0, making the voltage fall from 3.3V to 0V.