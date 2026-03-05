---
title: Module Bill of Materials
tags:
- tag1
- tag2
---

## Overview
This project is an ESP32-S3 based microcontroller system with integrated sensor interfaces and power regulation. The design features:

- **ESP32-S3-WROOM-1-N4** module as the main controller with WiFi/BLE connectivity
- **ADS1115 16-bit ADC** for precision analog sensor readings
- **NORPS-12 photoresistor** for light detection
- **Push button inputs** for user interface
- **Multiple LED indicators** for status output
- **USB and barrel jack power options** with built-in ESD protection



## Bill of Materials



| Part Name/Description | Unit Qty | Per Unit Cost | Total Cost | Manufacturer | Manufacturer Part # | Supplier | Vendor Part Number | Supplier Link | Supplier Part # | Date Ordered | # Ordered | # Received | Schematic Reference Designators |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10µF Ceramic Capacitor, 20%, 0805 package | 3 | $0.08 | $0.24 | Murata | GRM21BR61E106KA73L | DigiKey | 490-17609-1-ND | https://www.digikey.com/en/products/detail/kyocera-avx/TCJA106M010R0300/827200 | GRM21BR61E106KA73L | | | | C1, C9, C12 |
| 100µF Aluminum Electrolytic Capacitor, 20%, 25V, Radial | 1 | $0.21 | $0.21 | Nichicon | UHE1E101MED | DigiKey | 493-1749-ND | https://www.digikey.com/en/products/detail/kyocera-avx/TCJA107M006R0150/5323767 | UHE1E101MED | | | | Cin |
| 100nF Ceramic Capacitor, 10%, 50V, X7R, 0603 package | 6 | $0.03 | $0.18 | Samsung | CL10B104KB8NNNC | DigiKey | 1276-1012-1-ND | https://www.digikey.com/en/products/detail/vishay-sprague/TMCP1E104MTRF/10107437 | CL10B104KB8NNNC | | | | C3, C10, C11, C13, C20, C21 |
| 22µF Ceramic Capacitor, 20%, 6.3V, X5R, 0603 package | 2 | $0.12 | $0.24 | Murata | GRM188R60J226MEA0D | DigiKey | 490-10825-1-ND | https://www.digikey.com/en/products/detail/kyocera-avx/TAJB226K020RNJ/563789 | GRM188R60J226MEA0D | | | | C4, C5 |
| Green LED, 0603 package | 1 | $0.14 | $0.14 | LiteOn | LTST-C190GKT | DigiKey | 160-1444-1-ND | https://www.digikey.com/en/products/detail/liteon/LTST-C190GKT/269230 | LTST-C190GKT | | | | D1 |
| Red LED, 0603 package | 1 | $0.12 | $0.12 | Rohm | SML-D12U1WT86 | DigiKey | 511-1868-1-ND | https://www.digikey.com/en/products/detail/rohm-semiconductor/SML-D12U1WT86/5843853 | SML-D12U1WT86 | | | | D2 |
| RF DIODE PIN , 1A, 50V, 863-1145-1-ND | 5 | $0.32 | $0.32 | Skyworks | 863-1145-1-ND | DigiKey | 863-1145-1-ND | https://www.digikey.com/en/products/detail/skyworks-solutions-inc/SMP1345-040LF/2217455 | 1N5818 | | | | D3, U4, U7 |
| Power Barrel Connector Jack, 2.1mm, 12V | 1 | $0.69 | $0.69 | Kycon | KLDX-0202-BC | DigiKey | 2092-KLDX-0202-BC-ND | https://www.digikey.com/en/products/detail/kycon-inc/KLDX-0202-BC/9990097 | KLDX-0202-BC | | | | J1 |
| 10kΩ Thick Film Resistor, 1%, 0.1W, 0603 package | 8 | $0.01 | $0.08 | Yageo | RC0603FR-0710KL | DigiKey | 311-10KCRCT-ND | https://www.digikey.com/en/products/detail/stackpole-electronics-inc/RMCF0402FT10K0/1761433 | RC0603FR-0710KL | | | | R1, R4, R8, R9, R10, R11, R15, R18 |
| 1kΩ Thick Film Resistor, 1%, 0.1W, 0603 package | 4 | $0.01 | $0.04 | Yageo | RC0603FR-071KL | DigiKey | 311-1.0KCRCT-ND | https://www.digikey.com/en/products/detail/yageo/RC0603FR-071KL/726843 | RC0603FR-071KL | | | | R2, R3, R20, R21 |
| 22Ω Thick Film Resistor, 1%, 0.1W, 0603 package | 2 | $0.01 | $0.02 | Yageo | RC0603FR-0722RL | DigiKey | 311-22CRCT-ND | https://www.digikey.com/en/products/detail/yageo/RC0402FR-0722RL/726562 | RC0603FR-0722RL | | | | R5, R6 |
| 1.5kΩ Thick Film Resistor, 1%, 0.1W, 0603 package | 1 | $0.01 | $0.01 | Yageo | RC0603FR-071K5L | DigiKey | 311-1.5KCRCT-ND | https://www.digikey.com/en/products/detail/yageo/RC0402FR-071K5L/726519 | RC0603FR-071K5L | | | | R7 |
| Tactile Push Button Switch, SPST, 12V, 50mA | 2 | $0.46 | $0.92 | E-Switch | TL2233OA | DigiKey | EG4623-ND | https://www.digikey.com/en/products/detail/e-switch/TL2233OA/15220943 | TL2233OA | | | | SW1, SW2 |
| ESP32-S3-WROOM-1-N4 MCU Module | 1 | $5.06 | $5.06 | Espressif | ESP32-S3-WROOM-1-N4 | DigiKey | 1965-ESP32-S3-WROOM-1-N4CT-ND | https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639 | ESP32-S3-WROOM-1-N4 | | | | U1 
| 3.3V Step-Down Switching Regulator, 1A, 52kHz, D²PAK package | 1 | $1.85 | $1.85 | onsemi | LM2575D2T-3.3R4G | DigiKey | LM2575D2T-3.3R4GOS-ND | https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/2714705 | LM2575D2T-3.3R4G | | | | U2 |
| Photoresistor, NORPS-12 | 1 | $2.23 | $2.23 | Advanced Photonix | NORPS-12 | DigiKey | NORPS-12-ND | https://www.digikey.com/en/products/detail/advanced-photonix/NORPS-12/5039796 | NORPS-12 | | | | U3 |
| 16-Bit ADC Converter, MSOP-10 package | 1 | $5.12 | $5.12 | Texas Instruments | ADS1115IDGSR | DigiKey | 296-41793-1-ND | https://www.digikey.com/en/products/detail/texas-instruments/ADS1115IDGSR/2231567 | ADS1115IDGSR | | | | U5 |
| USB - micro B USB 2.0 Receptacle Connector 5 Position Surface Mount, Right Angle; Through Hole  | 1 | $0.78 | $0.78 | 	JAE Electronics | CONN RCPT USB2.0 MICRO B SMD R/A | DigiKey | 670-2675-1-ND | https://www.digikey.com/en/products/detail/jae-electronics/DX4R005JJ2R1800/3903229?s=N4IgTCBcDaIGwHYAMBaMiCsKCMKByAIiALoC%2BQA | USBLC6-2SC6 | | | | U8 |



## Resouce

The Bill of Material as a PDF download is available .
