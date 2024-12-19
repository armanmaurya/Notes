To use an **ultrasonic sensor** (such as the **HC-SR 04**) with an [Arduino](../Arduino.md), follow these steps. The sensor uses ultrasonic waves to measure the distance to an object by emitting a sound pulse and timing how long it takes to bounce back.
### Components:
- **HC-SR 04 Ultrasonic Sensor**
- **Arduino** (e.g., Uno, Nano, etc.)
- **Jumper Wires**
### Pin Description of HC-SR 04:
- **VCC**: Power supply (5 V)
- **GND**: Ground
- **TRIG**: Trigger pin (input to the sensor)
- **ECHO**: Echo pin (output from the sensor)
### Wiring Diagram:

| HC-SR 04 Pin | Arduino Pin      | Description              |
| ------------ | ---------------- | ------------------------ |
| VCC          | 5 V              | Power supply             |
| GND          | GND              | Ground                   |
| TRIG         | Pin 9 (Digital)  | Sends the trigger signal |
| ECHO         | Pin 10 (Digital) | Receives the echo signal |

### Wiring Summary:
1. **VCC** on the ultrasonic sensor connects to **5 V** on the Arduino.
2. **GND** on the sensor connects to **GND** on the Arduino.
3. **TRIG** on the sensor connects to **Pin 9** (or any other digital pin) on the Arduino.
4. **ECHO** on the sensor connects to **Pin 10** (or any other digital pin) on the Arduino.
### Example Code (Arduino):

```cpp
// Pin definitions
const int trigPin = 9;  // Trigger pin
const int echoPin = 10; // Echo pin

long duration;
int distance;

void setup() {
  // Initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  
  // Set the trigPin as an OUTPUT:
  pinMode(trigPin, OUTPUT);
  
  // Set the echoPin as an INPUT:
  pinMode(echoPin, INPUT);
}

void loop() {
  // Clear the trigPin by setting it LOW:
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  
  // Set the trigPin HIGH for 10 microseconds to send out the ultrasonic pulse:
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Read the time it takes for the echo to return:
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance (in cm) based on the speed of sound (343 m/s):
  distance = duration * 0.034 / 2;  // Divide by 2 for round trip

  // Print the distance to the Serial Monitor:
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");
  
  // Delay between readings:
  delay(500);
}
```

### Explanation:
1. **Trigger Pulse**: A 10-microsecond pulse is sent to the **TRIG** pin to start the measurement.
2. **Echo Pulse**: The sensor sends out an ultrasonic pulse, which reflects off an object, and the **ECHO** pin reads the time it takes for the pulse to return.
3. **Distance Calculation**: The distance is calculated based on the time it takes for the pulse to return using the formula:
   $$
   \text{Distance} = \frac{\text{duration} \times 0.034}{2}
   $$
   where `duration` is the time in microseconds, and the factor `0.034` represents the speed of sound in cm/μs (343 m/s = 0.034 cm/μs). The division by 2 accounts for the round trip of the sound wave.

### Key Points:
- **TRIG** pin sends a pulse to start the measurement.
- **ECHO** pin receives the returning pulse and measures the time it takes for the echo to return.
- The speed of sound is used to calculate the distance to the object based on the time measured.
- This setup works for distances typically between 2 cm and 400 cm.

With this wiring and code, you can measure distances using the ultrasonic sensor and output the readings to the Serial Monitor.

