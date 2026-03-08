---
title: Module Schematic
---

## Overview

This schematic is designed to show data of the rover by receiving information from subsystem A2. 


![schematic](A1_Current.png){style width:"350" height:"300;"}
**Figure ##:** Showing the schematic.


## Explanations

### ESP32

This is the brain of the subsystem. It will take information from the other subsystems and display it onto the OLED screen. The ESP32 will also use the buttons to send signals and information to the other subsystems to tell them to move. 

### OLED Screen

This screen will display serial information from other subsystems. It will also display what motiuon buttons are being pressed to show that it is trying to send commands to the rover. 

### Buttons

Other than the main debug, boot, and enable pins, there are 6 other buttons. 4 of these buttons are forward, bafckward, left, and right. The other 2 are spare buttons if they are needed or a button breaks. 

### LEDs

One LED is for debugging. The other is a LED that pairs with the other subsystems and their LED. This shows that the system is taking and recieving information. 

### Connections

The 8 pin connectors attach to the other subsystem of the controller. This enables both subsystems to give and recieve serial communication. 

## Resouces

The schematic as a PDF download is available [*here*](A1_Sub.pdf), and the Zip folder of the project [*here*](A1_Controller_Subsystem.zip).