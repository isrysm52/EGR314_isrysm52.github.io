---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
This block diagram is for the display and control ESP32 for the rover. This subsystem will use serial cvode to send information to the rover that the rover will then articulate to move and travel or do specific actions. Since this piece is not connected to the roiver, it will need a seperate power system with voltage regulators. THis will also need the OLED screen that will display serial information to the user. 

 
## A2 Block Diagram 

![A2 Block diagram ](ESP32_A1.drawio (1).png)


## Purpose

There are 9 pins, 1 OLED, and two LEDs that make the main part of the block diagram. 3 pins are for boot, enable, and debugging. These are the basics of a schematic with an esp32. The LEDs are also for debugging and communication throughout the systems. The 6 other pins are split between direction (4 pins) and spares. The spares are for if other pins do not work. 