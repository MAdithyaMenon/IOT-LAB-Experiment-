
# Experiment 4 — Raspberry Pi LED Blink

**Course:** IoT & Applications — PEMRT525  
**Batch:** MR 2K24 | S5 | JECC  
**Department:** Mechatronics Engineering  
**College:** Jyothi Engineering College (Autonomous)

## Aim
To write a Python program to blink an LED connected to Raspberry Pi GPIO17 (BCM) at 1 Hz frequency.

## Components Required

| Component | Quantity |
|---|---:|
| Raspberry Pi 3 / 4 | 1 |
| LED (Red / Green) | 1 |
| Resistor 220Ω | 1 |
| Breadboard | 1 |
| Jumper Wires (Female–Male) | 3 |

## Circuit Connections

| Raspberry Pi Pin | Component |
|---|---|
| GPIO17 (BCM) — Pin 11 | LED Anode (+) via 220Ω resistor |
| GND — Pin 6 | LED Cathode (−) |

```text
RPi GPIO17 (Pin 11) ──── 220Ω ──── LED(+) ──── LED(−) ──── GND (Pin 6)
```

## Program (Python)

```python
import RPi.GPIO as GPIO
import time

LED_PIN = 17  # BCM numbering

GPIO.setmode(GPIO.BCM)
GPIO.setup(LED_PIN, GPIO.OUT)

try:
    while True:
        GPIO.output(LED_PIN, GPIO.HIGH)
        time.sleep(0.5)

        GPIO.output(LED_PIN, GPIO.LOW)
        time.sleep(0.5)

except KeyboardInterrupt:
    print("Program stopped")

finally:
    GPIO.cleanup()
```

## Procedure

1. Connect the LED to GPIO17 (Physical Pin 11) through a 220Ω resistor.
2. Connect the LED cathode to GND (Physical Pin 6).
3. Open the Raspberry Pi terminal.
4. Create a Python file using `nano led_blink.py`.
5. Enter the program and save the file.
6. Run the program using:

```bash
python3 led_blink.py
```

7. Observe the LED blinking continuously.
8. Press Ctrl+C to stop the program.

## Result

The LED blinks continuously at 1 Hz frequency (500 ms ON and 500 ms OFF), confirming successful GPIO output control using Python on Raspberry Pi.
