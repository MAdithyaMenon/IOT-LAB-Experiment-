
# Experiment 3 — ESP32 LCD Display

**Course:** IoT & Applications — PEMRT525  
**Batch:** MR 2K24 | S5 | JECC  
**Department:** Mechatronics Engineering  
**College:** Jyothi Engineering College (Autonomous)

## Aim
To interface a 16×2 LCD display (I2C) with ESP32 and display text messages on both lines.

## Components Required

| Component | Quantity |
|---|---:|
| ESP32 Development Board | 1 |
| 16×2 LCD with I2C Module | 1 |
| Breadboard | 1 |
| Jumper Wires | 4 |
| USB Cable | 1 |

## Circuit Connections

| ESP32 Pin | I2C LCD Pin |
|---|---|
| 3.3V / 5V | VCC |
| GND | GND |
| GPIO21 (SDA) | SDA |
| GPIO22 (SCL) | SCL |

```text
ESP32          I2C LCD Module

3.3V / 5V ──── VCC
GND       ──── GND
GPIO21    ──── SDA
GPIO22    ──── SCL
```

## Library Required

`LiquidCrystal_I2C`

Install through Arduino IDE → Library Manager.

## Program

```cpp
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// I2C address: 0x27 or 0x3F
LiquidCrystal_I2C lcd(0x27, 16, 2);

int counter = 0;

void setup() {
  lcd.init();
  lcd.backlight();

  lcd.setCursor(0, 0);
  lcd.print("  JECC IoT Lab  ");
}

void loop() {
  lcd.setCursor(0, 1);
  lcd.print("Count: ");
  lcd.print(counter);
  lcd.print("   ");

  counter++;
  delay(1000);
}
```

## Procedure

1. Connect the I2C LCD to ESP32.
2. Connect SDA to GPIO21 and SCL to GPIO22.
3. Install the LiquidCrystal_I2C library.
4. Open Arduino IDE and upload the program.
5. Observe the LCD display.
6. Line 1 displays "JECC IoT Lab".
7. Line 2 displays a counter incrementing every second.
8. Adjust the contrast potentiometer if text is not visible.

## Result

The 16×2 LCD displays "JECC IoT Lab" on the first line and a live incrementing counter on the second line, confirming successful I2C communication between ESP32 and LCD.
