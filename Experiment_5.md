
# Experiment 5 — Raspberry Pi Switch Controlled LED

**Course:** IoT & Applications — PEMRT525  
**Batch:** MR 2K24 | S5 | JECC  
**Department:** Mechatronics Engineering  
**College:** Jyothi Engineering College (Autonomous)

## Aim
To interface a push-button switch with Raspberry Pi GPIO and control an LED based on switch input using Python.

## Components Required

| Component | Quantity |
|---|---:|
| Raspberry Pi 3 / 4 | 1 |
| LED (Red / Green) | 1 |
| Resistor 220Ω | 1 |
| Push-Button Switch | 1 |
| Breadboard | 1 |
| Jumper Wires (Female–Male) | 6 |

## Circuit Connections

| Raspberry Pi Pin | Component |
|---|---|
| GPIO17 (BCM) — Pin 11 | LED Anode (+) via 220Ω resistor |
| GND — Pin 6 | LED Cathode (−) |
| GPIO18 (BCM) — Pin 12 | Push-button terminal 1 |
| GND — Pin 14 | Push-button terminal 2 |

```text
RPi GPIO17 ──── 220Ω ──── LED(+) ──── LED(−) ──── GND

RPi GPIO18 ──── Button ──── GND
               (Pull-Up enabled)
```

## Program (Python)

```python
import RPi.GPIO as GPIO
import time

LED_PIN = 17
BUTTON_PIN = 18

GPIO.setmode(GPIO.BCM)

GPIO.setup(LED_PIN, GPIO.OUT)

GPIO.setup(
    BUTTON_PIN,
    GPIO.IN,
    pull_up_down=GPIO.PUD_UP
)

try:
    while True:
        button_state = GPIO.input(BUTTON_PIN)

        if button_state == GPIO.LOW:
            GPIO.output(LED_PIN, GPIO.HIGH)
        else:
            GPIO.output(LED_PIN, GPIO.LOW)

        time.sleep(0.05)

except KeyboardInterrupt:
    print("Program stopped")

finally:
    GPIO.cleanup()
```

## Procedure

1. Connect the LED to GPIO17 through a 220Ω resistor.
2. Connect the LED cathode to GND.
3. Connect one terminal of the push-button to GPIO18.
4. Connect the other terminal to GND.
5. Open the Raspberry Pi terminal.
6. Create a file using `nano switch_led.py`.
7. Enter the program and save it.
8. Run the program:

```bash
python3 switch_led.py
```

9. Press and hold the push-button to turn ON the LED.
10. Release the button to turn OFF the LED.
11. Press Ctrl+C to stop the program.

## Result

The LED turns ON when the push-button is pressed and turns OFF when released, confirming successful GPIO digital input reading using an internal pull-up resistor and output control on Raspberry Pi using Python.
