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

## **2. Microcontroller Research: ESP32-WROOM-32D**

| Feature | ESP32-WROOM-32D Specification | Project Requirement | Status |
|---------|-------------------------------|---------------------|--------|
| **Core Architecture** | Dual-core Xtensa LX6 240MHz | Single sensor reading |  **Exceeds** |
| **ADC Channels** | 18 channels (12-bit SAR) | 1 channel for photoresistor |  **Exceeds** |
| **UART Interfaces** | 3 UART controllers | 1 for subsystem communication |  **Exceeds** |
| **GPIO Pins** | 34 programmable GPIOs | Minimum 3 required |  **Exceeds** |
| **Operating Voltage** | 3.3V | Compatible with photoresistor circuit |  **Meets** |
| **WiFi/Bluetooth** |  Bluetooth 4.2 | Required for data transmission |  **Meets** |
| **Flash Memory** | 4MB | Ample for sensor firmware |  **Exceeds** |
| **SRAM** | 520KB | More than sufficient |  **Exceeds** |
| **Power Consumption** | 240MHz: ~160mA<br>Light-sleep: ~0.8mA | Suitable for rover operation |  **Meets** |
| **Package** | Surface-mount module | Meets EGR 314 requirements |  **Meets** |

## 3. Pinout Support for Photoresistor & UART

**Source:** ESP32-WROOM-32D Datasheet, Section 2: Pin Definitions, Table 2  
**Link:** [ESP32-WROOM-32D Datasheet (Espressif)](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32d_esp32-wroom-32u_datasheet_en.pdf)

<img width="505" height="525" alt="Image" src="https://github.com/user-attachments/assets/8ef3b636-0148-4625-af39-ad307d949317" />

*Figure 1: ESP32-WROOM-32D pinout.*
---
##  4. ADC Channels for Analog Light Sensing
**Source:** ESP32-WROOM-32D Datasheet, Section 4.4: ADC  
**Relevant Excerpt:**

> "The ESP32 integrates two 12-bit SAR ADCs (ADC1 and ADC2) supporting a total of 18 measurement channels. ADC1 is recommended for analog reading as it is not affected by WiFi/BT coexistence."

| ADC Channel | GPIO Pin | Our Use |
|------------|---------|---------|
| ADC1_CH0   | GPIO36  | Photoresistor analog input |

**Why this matters:** ADC1 is not shared with the WiFi radio, ensuring clean, stable light sensor readings even during wireless transmission.

---

## 5. UART Interfaces for Subsystem Communication
**Source:** ESP32-WROOM-32D Datasheet, Section 4.6: UART  
**Relevant Excerpt:**

> "The ESP32 has three UART interfaces (UART0, UART1, UART2). Each UART controller is independently configurable with baud rates up to 5 Mbps."

| UART | TX Pin | RX Pin | Our Use |
|------|--------|--------|---------|
| UART2 | GPIO17 | GPIO16 | Communication with other rover subsystems |

**Why this matters:** UART0 is reserved for programming/debug. UART2 provides a dedicated, interference-free serial link to the rest of the rover.

---

## 6. Team Role & Responsibilities

**Role:** Sensors and Communication Subsystem Lead

**Responsibilities:** I am responsible for the design, implementation, and integration of the photoresistor-based ambient light sensing system and the inter-subsystem UART communication link. For sensing, I selected a photoresistor voltage divider circuit interfaced to the ESP32's ADC1_CH0 (GPIO36), utilizing the 12-bit SAR ADC with WiFi-isolated channels to ensure noise-free analog readings.
