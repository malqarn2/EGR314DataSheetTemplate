## **1. Project Requirements Analysis**

Based on the underwater rover's block diagram and photoresistor subsystem requirements:

| Requirement | Quantity Needed | Justification |
|-------------|----------------|---------------|
| **ADC Channels** | 1 | Single photoresistor analog light sensor |
| **UART Interfaces** | 1 | Communication with other rover subsystems |
| **I²C/SPI Interfaces** | 0 | Photoresistor uses analog output, not digital bus |
| **GPIO Pins** | 3 minimum (ADC + UART) | ADC input + UART TX/RX |
| **Power Pins** | 2 | 3.3V and GND for sensor power |
| **Programming Pins** | 4 | EN, GPIO0, TX0, RX0 for programming |
| **Total Minimum Pins** | 9 | Basic functional requirement |
| **Additional Features** | WiFi/Bluetooth | Wireless environmental data transmission |

## **2. Microcontroller Research: ESP32-WROOM-32D**

| Feature | ESP32-WROOM-32D Specification | Project Requirement | Status |
|---------|-------------------------------|---------------------|--------|
| **Core Architecture** | Dual-core Xtensa LX6 240MHz | Single sensor reading |  **Exceeds** |
| **ADC Channels** | 18 channels (12-bit SAR) | 1 channel for photoresistor |  **Exceeds** |
| **UART Interfaces** | 3 UART controllers | 1 for subsystem communication |  **Exceeds** |
| **GPIO Pins** | 34 programmable GPIOs | Minimum 3 required |  **Exceeds** |
| **Operating Voltage** | 3.3V | Compatible with photoresistor circuit |  **Meets** |
| **WiFi/Bluetooth** | 802.11 b/g/n/e/i + Bluetooth 4.2 | Required for data transmission |  **Meets** |
| **Flash Memory** | 4MB | Ample for sensor firmware |  **Exceeds** |
| **SRAM** | 520KB | More than sufficient |  **Exceeds** |
| **Power Consumption** | 240MHz: ~160mA<br>Light-sleep: ~0.8mA | Suitable for rover operation |  **Meets** |
| **Package** | Surface-mount module | Meets EGR 314 requirements |  **Meets** |

## **3. Photoresistor-ESP32 Compatibility Research**

**Library and Code Research Findings:**
- **ESP32 ADC Library**: Built-in `analogRead()` function in Arduino framework
- **Example Code Available**: Multiple ESP32 photoresistor examples on GitHub and Arduino forums
- **Known Issues**: ESP32 ADC has non-linear characteristics (effective 9-10 bits of 12-bit ADC)
- **Solution**: Implement software calibration curve for accurate light measurements
- **No Major Compatibility Issues**: Simple voltage divider + ADC reading is well-documented

**Peripheral Communication Analysis:**
- **Photoresistor Interface**: Simple analog voltage (0-3.3V)
- **Required Functions**: Single `analogRead()` call per measurement
- **Initialization**: None required beyond ADC configuration
- **Calibration**: Software-based using known light intensities
- **Error Handling**: Basic range checking for valid ADC values (0-4095)

