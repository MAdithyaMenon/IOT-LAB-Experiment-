
# Experiment 2 — ESP32 Switch Controlled LED

**Course:** IoT & Applications — PEMRT525  
**Batch:** MR 2K24 | S5 | JECC  
**Department:** Mechatronics Engineering  
**College:** Jyothi Engineering College (Autonomous)

## Aim
To interface a push-button switch with ESP32 GPIO and control an LED based on switch input.

## Components Required

| Component | Quantity |
|---|---:|
| ESP32 Development Board | 1 |
| LED (Red / Green) | 1 |
| Resistor 220Ω | 1 |
| Push-Button Switch | 1 |
| Breadboard | 1 |
| Jumper Wires | 5 |
| USB Cable | 1 |

## Circuit Connections

| ESP32 Pin | Component |
|---|---|
| GPIO2 | LED Anode (+) via 220Ω resistor |
| GND | LED Cathode (−) |
| GPIO4 | Push-button terminal 1 |
| GND | Push-button terminal 2 |

```text
ESP32 GPIO4 ──── Button ──── GND
               (Internal Pull-Up)

ESP32 GPIO2 ──── 220Ω ──── LED(+) ──── LED(−) ──── GND
```

## Program

```cpp
#define LED_PIN 2
#define BUTTON_PIN 4

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}
```

## Procedure

1. Connect the LED to GPIO2 through a 220Ω resistor.
2. Connect the LED cathode to GND.
3. Connect one terminal of the push-button to GPIO4 and the other to GND.
4. Open Arduino IDE and select the correct board and COM port.
5. Upload the program.
6. Press and hold the push-button and observe the LED.
7. Release the button and observe the LED turning OFF.

## Result

The LED turns ON when the push-button is pressed and turns OFF when released, confirming successful GPIO digital input reading and output control on the ESP32.
