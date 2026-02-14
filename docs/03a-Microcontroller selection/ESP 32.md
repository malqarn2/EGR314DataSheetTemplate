## **1. Project Requirements Analysis**



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

## **2. Microcontroller Research: ESP32-S3-WROOM-1-N4**

| Feature | ESP32-S3-WROOM-1-N4 Specification	 | Project Requirement | Status |
|---------|-------------------------------|---------------------|--------|
| **Core Architecture** | Dual-core Xtensa LX6 240MHz | Single sensor reading |  **Exceeds** |
| **ADC Channels** | 20 channels (12-bit SAR) | 1 channel for photoresistor |  **Exceeds** |
| **UART Interfaces** | 5 UART controllers | 1 for subsystem communication |  **Exceeds** |
| **GPIO Pins** | 36 programmable GPIOs | Minimum 3 required |  **Exceeds** |
| **Operating Voltage** | 3.3V | Compatible with photoresistor circuit |  **Meets** |
| **WiFi/Bluetooth** | WiFi + Bluetooth 5 LE | Required for data transmission |  **Meets** |
| **Flash Memory** | 4MB | Ample for sensor firmware |  **Exceeds** |
| **SRAM** | 512KB | More than sufficient |  **Exceeds** |
| **Power Consumption** | 240MHz: ~160mA<br>Light-sleep: ~0.8mA | Suitable for rover operation |  **Meets** |
| **Package** | Surface-mount module | Meets EGR 314 requirements |  **Meets** |

## 3. Pinout Support for Photoresistor & UART

| Pin | Pin Name | Function | Our Use |
|-----|----------|----------|---------|
| 1 | GND | Ground | Power ground |
| 2 | 3V3 | 3.3V Power | Sensor power |
| 3 | EN | Enable | Programming/Reset |
| 4 | GPIO4 | ADC1_CH3 | Photoresistor analog input |
| 37 | GPIO16 | UART2_RXD | UART RX from rover |
| 38 | GPIO17 | UART2_TXD | UART TX to rover |
| 43 | GPIO43 | UART0_TXD | Programming TX |
| 44 | GPIO44 | UART0_RXD | Programming RX |
| 39 | GND | Ground | Ground |

<img width="551" height="677" alt="Image" src="https://github.com/user-attachments/assets/348c103f-a8e3-45bc-8ea1-3f4d0d0cc7e4" />

##  4. ADC Channels for Analog Light Sensing
**Source:** ESP32-WROOM-32D Datasheet, Section 4.4: ADC  
**Relevant Excerpt:**

> "The ESP32 integrates two 12-bit SAR ADCs (ADC1 and ADC2) supporting a total of 18 measurement channels. ADC1 is recommended for analog reading as it is not affected by WiFi/BT coexistence."

| ADC Channel | GPIO Pin | Our Use |
|------------|----------|---------|
| ADC1_CH3 | GPIO4 | Photoresistor analog input |


---

## 5. UART Interfaces for Subsystem Communication
**Source:** ESP32-WROOM-32D Datasheet, Section 4.6: UART  
**Relevant Excerpt:**

> "The ESP32 has three UART interfaces (UART0, UART1, UART2). Each UART controller is independently configurable with baud rates up to 5 Mbps."

| UART | TX Pin | RX Pin | Our Use |
|------|--------|--------|---------|
| UART2 | GPIO1 | GPIO3 | Communication with other rover subsystems |

**Why this matters:** UART0 is reserved for programming/debug. UART2 provides a dedicated, interference-free serial link to the rest of the rover.

---

## 6. Team Role & Responsibilities

**Role:** Sensors and Communication Subsystem Lead

**Responsibilities:** I am responsible for the design, implementation, and integration of the photoresistor-based ambient light sensing system and the inter-subsystem UART communication link using the ESP32-S3-WROOM-1-N4 module.

## 7. Final Microcontroller Choice

**My Selection:** ESP32-S3-WROOM-1-N4

**Rationale:** This microcontroller meets all project requirements with significant excess capacity. It provides 20 ADC channels (only 1 needed), 5 UART controllers (only 1 needed), and 36 GPIO pins (only 9 needed). The built-in USB programming eliminates need for external programmers, and ADC1 channels are isolated from WiFi interference for clean sensor readings.
