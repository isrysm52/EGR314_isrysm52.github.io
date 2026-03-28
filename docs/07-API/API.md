---
title: API
---

## Module Messages

The following sections document the messages sent and received from A1 subsystem. 

## My Role

My role is to send directional movement to each subsystem for them to receive and use that information. I will then receive the rest of the subsystem's messeges. 

Here are all the messeges and message types: 

| **message type byte 1 (uint8_t)** | **description** |
| -------: | :------- |
| 1  | Set steering angle in degrees - Sent from A1 to B2 as a response to user input. Upon recieving, B2 will move the rudders to the indicated position. |
| 2  | Set steering throttle percentage - Sent from A1 to B1 as a response to user input. Upon recieving, B1 will adjust the speed of the propellers to the desired percentage. |
| 3  | Set camera angle in degrees - Sent from A1 to C2 as a response to user input. Upon recieving, C2 will move the camera gimbal to the indicated position.  |
| 4  | Take picture. Sent from A1 to C1 as a response to user input. Upon recieving, C1 will take a picture and save it to an SD card. |
| 5  | Send speed data in m/s - Sent periodically from C3 to A1. Upon recieving, A1 will update the display. |
| 6  | Send distance data in cm - Sent periodically from D2 to A1. Upon recieving, A1 will update the display. |
| 7  | Send temperature data in celsius - Sent periodically from D1 to A1. Upon recieving, A1 will update the display. |
| 8  | Send camera angle data data in degrees - Sent periodically from C3 to C2. Used for gimbal stabilization. |
| 9  | Bluetooth communication error - Sent from both A2 and A3 as a broadcast as a result of failing 3 bluetooth heartbeat checks. Upon recieving, B2 sets angle to 0, B1 sets throttle to 0, and A1 shows an error on screen. |
| 10  | Bluetooth relay data - Sent between A2 and A3 (bidirectional). Contains a relayed message and relayed sender/reciever IDs. |
| 11 | Bluetooth heartbeat - Sent periodically from A2 to A3. Upon recieving, A3 will send this message back. If neither board recieves a heartbeat within a set interval, heartbeat failure will be recorded. |
| 12 | Rollcall - Debugging broadcast message triggered by pushing the 'debug' button on any subsystems configured to do so. Not all systems are expected to be able to trigger rollcall, but all systems must respond to it. Lights up LEDs for a set interval on every subsystem that recieves it. |


## Messeges Sent

Message type 1 - Set Steering Angle

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Angle |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | A | E |1 | 0 |
| Max Value | A | E | 1| 255|
| Example | A | E |1 | 125 | 

Message type 2 - Set Throttle Percentage:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Throttle |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | A | D |2 | 0 |
| Max Value | A | D | 2| 255|
| Example | A | D |2 | 125 | 

Message type 3 - Set Camera Angle:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|**Byte 5**|
| :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Yaw | Pitch |
| Variable Type | char | char | uint8_t | int8_t | int8_t |
| Min Value | A | G |5 | -128 | -128 |
| Max Value | A | G | 5| 127| 127 |
| Example | A | G |5 | 125 | 90 |

Message type 4 - Take Photo:

||**Byte 1** |**Byte 2**|**Byte 3**|
| :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type |
| Variable Type | char | char | uint8_t |
| Min Value | A | F |4 |
| Max Value | A | F | 4|
| Example | A | F |4 |



## Messeges Received

Message type 5 - Send Speed Data:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Speed |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | H | A |5 | 0 |
| Max Value | H | A | 5| 255|
| Example | H | A |5 | 125 | 

Message type 6 - Send Distance Data:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Distance |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | J | A |6 | 0 |
| Max Value | J | A | 6| 255|
| Example | J | A |6 | 125 | 

Message type 7 - Send Temperature Data:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Temperature |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | I | A |7 | 0 |
| Max Value | I | A | 7| 255|
| Example | I | A |7 | 125 | 

Message type 8 - Stabilize Arm:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|**Byte 5**|
| :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Yaw | Pitch |
| Variable Type | char | char | uint8_t | uint8_t | uint8_t |
| Min Value | H | G | 8 | 0 | 0 |
| Max Value | H | G | 8 | 255| 255 |
| Example | H | G | 8 | 125 | 90 |

Message type 9 - Bluetooth Error:

||**Byte 1** |**Byte 2**|**Byte 3**|
| :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type |
| Variable Type | char | char | uint8_t |
| Min Value | B | A | 9 |
| Max Value | C | G | 9 |
| Example | C | G | 9 |

Message type 10 - Bluetooth Relay:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|**Byte 5**|**Byte 6**|**Byte 7**|
| :-------: | :-------: | :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Relay_Sender | Relay_Reciever | Data_1 | Data_2 |
| Variable Type | char | char | char | char | char | char | CHAR |
| Min Value | B | B | 10 | A | A | 00000000 | 00000000 |
| Max Value | C | C | 10 | J | X | 11111111 | 11111111 |
| Example | C | B | 10 | I | A | 00110101 | 00000000 |

Message type 11 - Bluetooth Heartbeat:

||**Byte 1** |**Byte 2**|**Byte 3**|
| :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type |
| Variable Type | char | char | uint8_t |
| Min Value | B | B |11 |
| Max Value | C | C | 11|
| Example | B | C |11 |

Message type 12 - Rolecall:

||**Byte 1** |**Byte 2**|**Byte 3**|
| :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type |
| Variable Type | char | char | uint8_t |
| Min Value | A | X |12 |
| Max Value | J | X | 12|
| Example | A | J |12 |


