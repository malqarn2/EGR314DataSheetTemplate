---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6"> Mohammed Ali Datasheet </font><br>
as part of<br>
<font size= "8"> Project Name </font><br>
for<br>
<font size= "5"> Team 308 </font><br>

**Submission: 1, 18, 2026**
</center>


## Introduction

This datasheet documents the design and implementation of my subsystem for the EGR 314 team project. Its purpose is to explain the hardware, software, communication protocol, and design decisions used in my module so that another student, teammate, or instructor can understand how it works and how it connects to the larger team system. This page is meant to serve as both a technical reference and a record of my individual contribution to the project.


### Project Summary

Our team project is a submarine system made up of multiple subsystems that communicate with each other through a UART-based daisy chain. Each team member is responsible for one subsystem, and all subsystems work together by sending structured packets with a shared communication format. The purpose of the overall project is to allow the submarine system to sense conditions, exchange information, and respond through coordinated subsystem behavior.

My part of the project is the light subsystem. The purpose of my subsystem is to detect whether there is light or there is not light and communicate that information to the rest of the system. This gives the submarine project environmental input that can be used by the control subsystem and other modules during team integration. My subsystem contributes to the project by measuring light, converting that reading into a simple status, and sending that status using the agreed packet format.

For more details about the full team system and how all subsystems fit together, see the linked team report.

For more details about the complete team design and how all subsystems fit together, see the linked team report.
* Add context that ties into the link to your [team report.](https://egr314-s-2026-308.github.io/)

### My Contribution

My contribution to the team project is the light sensor subsystem. I designed and implemented the subsystem hardware around the ESP32-S3 and used a photoresistor together with an ADS1115 external ADC to measure ambient light. My subsystem determines whether light is present or not present, then communicates that information to the team system.

On the software side, I wrote the code needed to read the sensor, convert the reading into a simple light or no-light status, and send messages across the UART communication chain. I also worked on packet formatting, message handling, and subsystem responses so that my board could communicate correctly with the control subsystem and the rest of the project. In addition, I updated the datasheet and API documentation for my subsystem so that the hardware and communication behavior were clearly explained.

This datasheet is organized so that a reader can review the hardware design, bill of materials, API/message structure, and implementation details of the light subsystem. To review the details of the material used to construct the subsection, see the **BOM** section of the datasheet.
