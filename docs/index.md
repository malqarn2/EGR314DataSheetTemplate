---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6"> Mohammed Ali Datasheet </font><br>
as part of<br>
<font size= "8"> Rugged Surveyor </font><br>
for<br>
<font size= "5"> Team 308 </font><br>

**Submission: 1, 18, 2026**
</center>


## Introduction

- This datasheet is to help define the light sensing subsystem for the Rugged Surveyor submarine project. My subsystem is responsible for detecting whether there is light or there is no light in the surrounding environment. This is done using a photoresistor and an ADS1115 external ADC connected to the ESP32-S3. The purpose of this subsystem is to provide light information to the rest of the submarine system so that the control subsystem can use that data during operation. As part of the overall project, our goal is to create a robotic submarine that can explore environments and collect useful environmental data while reducing the need for humans to enter dangerous areas directly.

### Project Summary

- This project is to create a full robotic system that can function as an underwater survey submarine. My team is building a submarine that can measure environmental conditions such as temperature and light levels while also supporting movement and communication between multiple subsystems. My contribution is the light subsystem, which detects whether light is present or not present and communicates that information to the rest of the team using the shared UART message protocol.

For more details about the complete team design and how all subsystems fit together, see the linked team report.
* Add context that ties into the link to your [team report.](https://egr314-s-2026-308.github.io/)

### My Contribution

- My contribution to this project is the light sensor subsystem. I designed and implemented the hardware and software needed to detect ambient light and convert it into a usable system status. My subsystem uses a photoresistor with an ADS1115 external ADC to read light levels and determine whether there is light or no light. I also developed the communication portion of the subsystem so it can send status and sensor messages to the control subsystem and respond correctly to incoming requests. This allows my subsystem to support the larger submarine project by providing environmental light information to the team system.
