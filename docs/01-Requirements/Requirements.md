---
title: Module's Requirements
---

## Module Requirements
For this project I'm focusing on the photo/light sensor system to measure underwater light levels for environmental analysis.
| Requirement Description | Measure of Threshold | Target Measure | Stretch Requirement (Y-N) |
|---|---|---|---|
| Surface mounted microcontroller | 1 PIC or ESP microcontroller | 8-bit PIC or ESP32 | No |
| Surface mounted, 3.3V switching power regulator | 3.2 Volts | 3.3 Volts | No |
| Wireless Communication | Able to send or receive a Wi-Fi data | Send and receive Wi-Fi Data to MQTT | Yes |
| Light sensor type | Photoresistor (LDR) | Photoresistor (LDR) with voltage divider | No |
| Sensor connection | Analog voltage to ADC pin | Stable analog signal with noise filtering | No |
| Waterproof housing | Epoxy coated sensor | Sealed tube with transparent end | No |
| Depth rating | 1 meter submersion | 1 meter submersion | Yes |
| Measurement range | Detect light in the dark | 0–1,000 lux (approximate) | Yes |
| Accuracy | Distinguish light levels | 25% of actual lux | Yes |
| Power consumption | < 10 mA | < 5 mA | Yes |
| Calibration | Manual calibration in code | Two point calibration (dark/bright) | Yes |
| Failure detection | Visual inspection | Timeout check in software | No |
