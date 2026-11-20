# Digital LED Control & Effects Station (ESP32)

An interactive LED dimmer and lighting effects controller built on an **ESP32** using a **quadrature rotary encoder with push button** and an **I2C OLED display (SSD1306)**, with perceptual gamma correction (`2.2`) and a live OLED status/progress UI.

## Features
- **Rotate Knob:** Adjusts brightness (`0–100%`) in Manual mode or effect speed (`10–100%`) in Effects modes.
- **Short Press (`SW`):** Cycles through **4 modes** (`MANUAL DIM`, `BREATHE`, `STROBE`, `CANDLE`).
- **Long Press (`SW`, ~0.8s):** Toggles master **ON / OFF** standby state.
- **Perceptual Gamma Correction:** Applies `pow(x, 2.2)` so low-end dimming feels smooth to the human eye.
- **Live OLED Dashboard:** Shows mode, power/speed percentage, ON/OFF badge, and a progress bar.

## Hardware Required
- ESP32 development board
- Rotary encoder with push switch (4-pin breakout: `GND`, `SW`, `CLK`, `DT`)
- 0.96" I2C OLED display (`128x64`, SSD1306, address `0x3C`)
- 1x LED
- 1x `220–330 Ω` current-limiting resistor
- Breadboard and jumper wires

## Pinout / Wiring

### Rotary Encoder -> ESP32
| Encoder Pin | ESP32 Pin | Notes |
| :--- | :--- | :--- |
| `GND` | `GND` | Common ground |
| `SW` | `GPIO 27` | Uses internal `INPUT_PULLUP` |
| `CLK` | `GPIO 32` | Uses internal `INPUT_PULLUP` |
| `DT` | `GPIO 33` | Uses internal `INPUT_PULLUP` |

### LED -> ESP32
- `GPIO 25` -> `220–330 Ω` resistor -> LED Anode (`+`)
- LED Cathode (`-`) -> `GND`

### OLED Display (I2C) -> ESP32
| OLED Pin | ESP32 Pin |
| :--- | :--- |
| `GND` | `GND` |
| `VCC` | `3.3V` |
| `SCL` | `GPIO 22` |
| `SDA` | `GPIO 21` |

## Software & Libraries
- **Arduino IDE** with **ESP32 board support** installed
- **Adafruit GFX Library**
- **Adafruit SSD1306**

## How to Run
1. Wire the components according to the tables above.
2. Open `firmware/esp32_led_fx_station/esp32_led_fx_station.ino` in the Arduino IDE.
3. Install **Adafruit GFX** and **Adafruit SSD1306** via **Sketch -> Include Library -> Manage Libraries**.
4. Select your ESP32 board and COM port, then click **Upload**.

## License
Released under the [MIT License](LICENSE).
