---
title: Module's Block Diagram

---

## Overview

- The photoresistor module measures light levels underwater at 3.3V power. It sends analog voltage readings to the IC  which converts them to digital light values to the rover's brain (ESP32) . These readings are shared with other rover systems through wireless communication for environmental monitoring.


## Mo's Block Diagram 


<img width="811" height="461" alt="Image" src="https://github.com/user-attachments/assets/f4eb72e0-cc43-4a5c-b74d-e321315872d0" />

or as [Mo314 Block diagram.drawio.pdf](https://github.com/user-attachments/files/25811765/Mo314.Block.diagram.drawio.pdf)

## **Product requirements**
- My block diagram meets the product requirements because it supports the complete job of the light subsystem. The project requires sensor input, subsystem communication, and integration into the full submarine system. My design satisfies the sensing requirement by using a photoresistor to measure light. It satisfies the data-conversion requirement by using the ADC to translate the analog sensor output into a digital value. It satisfies the control and communication requirement by using the ESP32 to process that information and send it through the agreed UART packet format. It also satisfies the integration requirement by showing how the subsystem connects to the upstream and downstream communication path used by the team.
