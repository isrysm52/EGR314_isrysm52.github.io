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


## A2 Block Diagram Updated

![A2 Block diagram Updated ](ESP32_A1.drawio (2).png)


## Purpose

There are 9 pins, 1 OLED, and two LEDs that make the main part of the block diagram. 3 pins are for boot, enable, and debugging. These are the basics of a schematic with an esp32. The LEDs are also for debugging and communication throughout the systems. The 6 other pins are split between direction (4 pins) and spares. The spares are for if other pins do not work. 

## Decicions for the Changes

Everything was still the same after making the PCB/ The block diagram had the components it needed and there was no change in the main part. The change comes in with the buttons. The spare buttons were used, not because of other buttons being broken, because we needed more prompts from the A1 subsystem for movements of other subsystems. This came to place because the team kept growing even after this assignment. 