# Board Reference

This repository stores notes, pin mappings, and PlatformIO board information for several Arduino and ESP32 boards.

## Contents
- [Quick notes](#quick-notes)
- [PlatformIO setup](#platformio-setup)
- [Board references](#board-references)
- [Sensor and peripheral notes](#sensor-and-peripheral-notes)

## Quick notes
- Some boards require holding the boot/program button during upload.
- The ADS1115 can be unreliable when used with an OLED display on the Heltec WiFi LoRa board if the hardware I2C setup conflicts.
- PlatformIO is the intended tool for these examples and board definitions.

## PlatformIO setup
Use VS Code with PlatformIO.

The project includes the file [platformio.ini](platformio.ini), which defines multiple board environments such as:
- `esp32dev`
- `heltec_wifi_lora_32`
- `heltec_wifi_lora_32_V2`
- `lolin32`
- `TTGOBatteryOLED`
- `featheresp32`
- `esp32-s3-devkitc-1-n16r8v`
- `nanoatmega328`

## Board references

### Adafruit HUZZAH32
Board name: Adafruit HUZZAH32 ESP32 Feather Board

PlatformIO board type: `featheresp32`

Notes:
- Built-in LED is on pin 13 as `LED_BUILTIN`.
- No button press is required for normal upload.

![Top pinout](docs/AdafruitHUZZAH32-ESP32FeatherPinoutTop.jpg)
![Bottom pinout](docs/AdafruitHUZZAH32-ESP32FeatherPinoutBottom.jpg)
![Diagram](docs/AdafruitHuzzah32PinDiagram.png)

### Arduino Nano
Board name: Arduino Nano (ATmega328)

PlatformIO board type: `nanoatmega328`

![Pinout](docs/arduino-nano-pinout.png)

### ESP32 DevKitC v4
Board name: ESP32 DevKitC v4

PlatformIO board type: `esp32dev`

Notes:
- Includes an external antenna connection.

![Pinout 1](docs/ESP32-DEV-KIT-DevKitC-v4-pinout-mischianti.png)
![Pinout 2](docs/esp32-devkitC-v4-pinout.png)

### WEMOS LOLIN32
Board name: WEMOS LOLIN32

PlatformIO board type: `lolin32`

OLED connections:
- Clock: 4
- Data: 5
- Reset: 16

![Top view](docs/WemosESP32OLEDTop.jpg)
![Bottom view](docs/WemosESP32OLEDBottom.jpg)
![Pinout](docs/WemosESP32OLEDPinout.jpg)

### WEMOS LOLIN32 V1.0.0
Board name: WeMos LOLIN32 V1.0.0

PlatformIO board type: not specified in the old notes

![Top view](docs/ESP32WeMosLOLIN32Top.jpg)
![Bottom view](docs/ESP32WeMosLOLIN32Bottom.jpg)
![Pinout](docs/ESP32WeMosLOLIN32Pinout.png)

### WEMOS D1 Mini Pro
Board name: WeMos D1 Mini Pro

PlatformIO board type: not specified in the old notes

![Pinout](docs/wemos_d1_mini_pro_pinout.png)

### Heltec WiFi LoRa 32 V1
Board name: Heltec WiFi LoRa 32 V1

PlatformIO board type: `heltec_wifi_lora_32`

Notes:
- Programming may require holding the PRG button near the antenna.

I2C connections:
- SCL: 22
- SDA: 21

OLED connections:
- Clock: 15
- Data: 4
- Reset: 16

![Pinout](docs/WiFi-LORA-32-pinout-Diagram.png)

### Heltec WiFi LoRa 32 V2
Board name: Heltec WiFi LoRa 32 V2

PlatformIO board type: `heltec_wifi_lora_32_V2`

Notes:
- Programming may require holding the PRG button near the antenna.
- Unresolved issues were noted when using a second I2C device with the OLED.

I2C connections:
- SCL: 22
- SDA: 21

OLED connections:
- Clock: 15
- Data: 4
- Reset: 16

![Pinout](docs/WIFI_LoRa_32_V2PinDiagram.png)

### TTGO ESP32 with battery holder and OLED
Board name: TTGO ESP32 with built-in battery holder and OLED

PlatformIO board type: `TTGOBatteryOLED`

OLED connections:
- Clock: 4
- Data: 5
- Reset: not connected

![Board view](docs/ESP32OledBatteryHolder.jpg)
![Pinout](docs/ESP32OledBatteryHolderPinout.jpg)

### ESP32-S3-N16R8 with onboard WS2812
Board name: ESP32-S3-N16R8 Black board with onboard WS2812

PlatformIO board type: `esp32-s3-devkitc-1-n16r8v`

Notes:
- Dual-core ESP32-S3
- 16 MB flash
- 8 MB PSRAM
- 512 KB SRAM
- UART COM connection is reversed compared to other boards
- Onboard WS2812 is connected to GPIO48
- The custom board definition in this repository is intended to enable the SRAM configuration needed for this board

![Board view](docs/esp32-S3-DevKitC-1.jpg)
![Board view with HW678](docs/esp32-S3-DevKitC-1-HW678.jpg)
![Original pinout](docs/esp32-S3-DevKitC-1-original-pinout-high.png)

## Sensor and peripheral notes

### Adafruit ADS1115
- I2C address: `0x48`
- Supply range: 2.0V to 5.5V DC
- 16-bit ADC with up to 860 samples/second
- Can be configured for four single-ended inputs or two differential inputs

![Diagram](docs/AdafruitADS1015ADS1115PinDiagram.jpg)

More information: [Adafruit ADS1115](https://www.adafruit.com/product/1085)

### BME280 / BMP280
- I2C address: `0x76` or `0x77` (with jumper change)
- Supply range: 1.8V to 5V DC
- BME280 includes pressure, temperature, and humidity
- BMP280 includes pressure and temperature

![Diagram](docs/BMP280.jpg)

More information: [Adafruit BME280 guide](https://learn.adafruit.com/adafruit-bme280-humidity-barometric-pressure-temperature-sensor-breakout)

### MPRLS
- I2C address: `0x18` (fixed)
- Supply range: 2.0V to 5.5V DC
- Pressure sensing range: 0-25 PSI

![Diagram](docs/MPRLS3965-00.jpg)

More information: [Adafruit MPRLS](https://www.adafruit.com/products/3965) or [SparkFun MPRLS](https://www.sparkfun.com/products/16476)

### LSM303DLHC
- I2C address: `0x19` and `0x1E`
- Supply range: 2.0V to 5.5V DC
- Triple-axis accelerometer + magnetometer (compass)
- This board appears to be a clone and was not verified in use

![Module view](docs/LSM303DLHCe-Compass3AxisAccelerometerAnd3AxisMagnetometerModule.jpg)
![Module view 2](docs/LSM303DLHCe-Compass3AxisAccelerometerAnd3AxisMagnetometerModule61VO3bK8u+L._AC_SX679_.jpg)

More information: [Adafruit LSM303](https://www.adafruit.com/product/1120) and [LSM303 breakout guide](https://learn.adafruit.com/lsm303-accelerometer-slash-compass-breakout/coding)

## Final note
Keep at it.