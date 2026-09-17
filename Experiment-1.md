
# Experiment: To Blink an LED Connected to ESP32 GPIO at 1 Hz Using Arduino IDE

## 1. Aim

To blink an LED connected to an ESP32 GPIO pin at a frequency of **1 Hz** using the **Arduino IDE**.

---

## 2. Apparatus Required

| Sl. No. | Component                 |    Quantity |
| ------- | ------------------------- | ----------: |
| 1       | ESP32 Development Board   |           1 |
| 2       | LED                       |           1 |
| 3       | 220 Ω resistor            |           1 |
| 4       | Breadboard                |           1 |
| 5       | Jumper wires              | As required |
| 6       | USB cable                 |           1 |
| 7       | Computer with Arduino IDE |           1 |

---

## 3. Theory

An LED can be controlled by an ESP32 by connecting it to one of the ESP32's GPIO pins.

A frequency of **1 Hz** means that the LED completes **one complete ON-OFF cycle every second**.

Therefore, the time period is:

$$
T = \frac{1}{f}
$$

For:

$$
f = 1\text{ Hz}
$$

$$
T = \frac{1}{1} = 1\text{ second}
$$

For equal ON and OFF durations:

* ON time = 0.5 s = 500 ms
* OFF time = 0.5 s = 500 ms

Thus, the LED is turned ON for 500 ms and OFF for 500 ms.

---

## 4. Circuit Connections

Use **GPIO 2** of the ESP32 for controlling the LED.

| ESP32 Pin       | Connection                     |
| --------------- | ------------------------------ |
| GPIO 2          | 220 Ω resistor → LED anode (+) |
| LED cathode (-) | GND                            |

### Circuit Diagram

```text
          ESP32
       +-----------+
       |           |
GPIO 2 |-----------|----[220 Ω]---->|---- GND
       |           |                LED
       +-----------+
```

> **Note:** The longer leg of a typical LED is the anode (+), and the shorter leg is the cathode (-). The resistor is used to limit the LED current.

---

## 5. Software Required

* Arduino IDE
* ESP32 board package installed in Arduino IDE

---

## 6. Algorithm

1. Start the program.
2. Define GPIO 2 as the LED pin.
3. Configure GPIO 2 as an output.
4. Turn the LED ON.
5. Wait for 500 ms.
6. Turn the LED OFF.
7. Wait for 500 ms.
8. Repeat steps 4–7 continuously.

---

## 7. Arduino Program

```cpp
// Experiment: Blink an LED at 1 Hz using ESP32

#define LED_PIN 2

void setup() {
  // Configure GPIO 2 as an output
  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  // Turn LED ON
  digitalWrite(LED_PIN, HIGH);
  delay(500);

  // Turn LED OFF
  digitalWrite(LED_PIN, LOW);
  delay(500);
}
```

---

## 8. Program Explanation

### `#define LED_PIN 2`

Defines GPIO 2 as the pin connected to the LED.

### `pinMode(LED_PIN, OUTPUT);`

Configures GPIO 2 as an output pin.

### `digitalWrite(LED_PIN, HIGH);`

Sets GPIO 2 HIGH and turns the LED ON.

### `delay(500);`

Keeps the LED ON for **500 milliseconds (0.5 seconds)**.

### `digitalWrite(LED_PIN, LOW);`

Sets GPIO 2 LOW and turns the LED OFF.

### `delay(500);`

Keeps the LED OFF for **500 milliseconds (0.5 seconds)**.

The `loop()` function executes repeatedly, producing a continuous ON-OFF cycle.

---

## 9. Procedure

1. Connect the ESP32 development board to the computer using a USB cable.
2. Connect the LED to GPIO 2 through a 220 Ω resistor.
3. Connect the cathode of the LED to GND.
4. Open the Arduino IDE.
5. Select the appropriate ESP32 board under **Tools → Board**.
6. Select the appropriate COM/serial port under **Tools → Port**.
7. Enter the above Arduino program.
8. Compile the program using the **Verify** option.
9. Upload the program to the ESP32.
10. Observe the LED.
11. The LED should turn ON for 0.5 seconds and OFF for 0.5 seconds continuously.

---

## 10. Observation

| Parameter                |   Value |
| ------------------------ | ------: |
| LED ON time              |  500 ms |
| LED OFF time             |  500 ms |
| Total time for one cycle | 1000 ms |
| Frequency                |    1 Hz |
| Duty cycle               |     50% |

---

## 11. Result

The LED connected to **GPIO 2 of the ESP32** was successfully blinked at a frequency of **1 Hz** using the Arduino IDE.

---

## 12. Precautions

1. Always connect a suitable current-limiting resistor in series with the LED.
2. Check the LED polarity before connecting the circuit.
3. Ensure that the ESP32 GND and LED circuit are properly connected.
4. Select the correct ESP32 board and COM port before uploading the program.
5. Do not apply voltages higher than the GPIO pin's permitted level.
6. Verify the circuit connections before powering the ESP32.

---


