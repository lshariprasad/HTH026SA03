## 📍 Pinouts (Current Prototype Pin Assignment)

> Verify all pins against your exact board variant before final assembly.

### 🖥️ Main ESP32 — Monitoring & Control Node

| Function | GPIO | Notes |
|---|---|---|
| TFT CS | 15 | ST7735 |
| TFT DC | 2 | ST7735 |
| TFT RST | 4 | ST7735 |
| TFT SCLK | 18 | SPI clock |
| TFT MOSI | 23 | SPI data |
| Button 1 (B1) | 12 | Overview page |
| Button 2 (B2) | 13 | Energy page |
| Button 3 (B3) | 14 | Lighting page |
| Button 4 (B4) | 26 | AUTO / MANUAL mode |
| Buzzer | 27 | Alerts |

> All pins above are **RESERVED** on the Main ESP32.

### ⚡ Energy Node — Mini ESP32-C3 #1

| Function | GPIO | Notes |
|---|---|---|
| Current Sensor OUT | 3 | ADC input |
| Voltage Sensor OUT | 4 | ADC input |

### 💡 Lighting Node — Mini ESP32-C3 #2

| Function | GPIO | Notes |
|---|---|---|
| LDR | 0 | Ambient light (ADC) |
| Potentiometer | 1 | Idle brightness (ADC) |
| LED PWM | 3 | Drive via transistor/MOSFET, not directly |
| Vibration Sensor | 4 | Digital input |
| PIR | 5 | Digital input |
| Ultrasonic TRIG | 6 | Digital output |
| Ultrasonic ECHO | 7 | Use level shifter / divider if 5 V |
| OLED SDA | 8 | I2C |
| OLED SCL | 9 | I2C |
| Brightness Adjust Button | 10 | 20 → 40 → 60 → 80 → 100 → repeat |

### ⚠️ Pin Safety Notes

- Exact GPIO availability depends on the ESP32-C3 board variant.
- Do not feed 5 V logic directly into any ESP32 / ESP32-C3 GPIO.
- HC-SR04-class ECHO outputs need a level shifter or resistor divider.
- Never drive high-power LEDs directly from a GPIO; use a MOSFET/transistor driver.
- ADC inputs must never exceed the ESP32-C3 input limit; scale down with a divider if needed.
- Main ESP32 GPIO 2, 12, 15 are boot-strapping pins; disconnect peripherals on them if the board fails to boot.
- ESP32-C3 GPIO 8, 9 are strapping pins; check that the OLED wiring doesn't interfere with boot.
