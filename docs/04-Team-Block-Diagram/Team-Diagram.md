---
title: Block Diagram, Protocol, and Message Structure
---

## Team Block Diagram
![Diagram](files/Team201_BlockDiagram.png)
**Figure 1:** Block Diagram of all subsystem modules in subgroups A, B, C, D with connectors and communication chain. PDF version [*here*](files/Team201_BlockDiagram.pdf)

## Sequence Diagram of Team Communication

``` mermaid
sequenceDiagram
  autonumber
  actor U as InPersonUser
  participant I as Isaac<br/>Controller
  box Blue
  participant M as Michael<br/>Controller Transceiver
  participant N as Neel<br/>Drone Transceiver
  end
  participant J as Jacob<br/>Steering
  participant P as K Phang<br/>Throttle
  participant H as Hafsa<br/>Gyroscope & Accelerometer
  participant A as Austin<br/>Camera Arm
  participant L as Levi<br/>Camera
  participant S as Seth<br/>Distance Sensor
  participant K as Kelton<br/>Temperature Sensor

  Note over M,N: Bluetooth Low Energy Communication

  U-->>I: Steer Drone
  I->>M: Isaac to Jacob<br/>Steer Drone to 45 degrees
  M->>N: Isaac to Jacob<br/>Steer Drone to 45 degrees
  N->>J: Isaac to Jacob<br/>Steer Drone to 45 degrees
  J->>J: Adjust Steering Servo to<br>45 degrees, Trash Message

  U-->>I: Throttle Drone
  I->>M: Isaac to K<br/>Throttle Drone to 80%
  M->>N: Isaac to K<br/>Throttle Drone to 80%
  N->>J: Isaac to K<br/>Throttle Drone to 80%
  J->>P: Isaac to K<br/>Throttle Drone to 80%
  P->>P: Adjust Motor Speed to 80%,<br/> Trash Message

  U-->>I: Turn Camera
  I->>M: Isaac to Austin<br/>Camera to 24 degrees
  M->>N: Isaac to Austin<br/>Camera to 24 degrees
  N->>J: Isaac to Austin<br/>Camera to 24 degrees
  J->>P: Isaac to Austin<br/>Camera to 24 degrees
  P->>H: Isaac to Austin<br/>Camera to 24 degrees
  H->>A: Isaac to Austin<br/>Camera to 24 degrees
  A->>A: Adjust Camera Servo to<br/>24 degrees, Trash Message

  U-->>I: Take Picture
  I->>M: Isaac to Levi<br/>Take Photo
  M->>N: Isaac to Levi<br/>Take Photo
  N->>J: Isaac to Levi<br/>Take Photo
  J->>P: Isaac to Levi<br/>Take Photo
  P->>H: Isaac to Levi<br/>Take Photo
  H->>A: Isaac to Levi<br/>Take Photo
  A->>L: Isaac to Levi<br/>Take Photo
  L->>L: Take and Save Image,<br/>Trash Message

  M-->>I: Micheal to Isaac<br/>Bluetooth communication error
  I->>I: Display "No Connection" error,<br/>Trash Message

  N-->>J: Neel to K<br/>Bluetooth communication error
  J->>J: Adjust Steering Servo to<br>0 degrees
  J->>P: Neel to K<br/>Bluetooth communication error
  P->>P: Adjust Motor Speed to 0%,<br/> Trash Message

  M-->>N: Micheal to Micheal<br/>Bluetooth heartbeat
  N->>N: Register Heartbeat
  N->>M: Micheal to Micheal<br/>Bluetooth heartbeat
  M->>M: Register Heartbeat,<br/> Trash Message

  I-->>M: Issac to Kelton<br/>Rolecall
  M->>M: Turn on LED
  M->>N: Issac to Kelton<br/>Rolecall
  N->>N: Turn on LED
  N->>J: Issac to Kelton<br/>Rolecall
  J->>J: Turn on LED
  J->>P: Issac to Kelton<br/>Rolecall
  P->>P: Turn on LED
  P->>H: Issac to Kelton<br/>Rolecall
  H->>H: Turn on LED
  H->>A: Issac to Kelton<br/>Rolecall
  A->>A: Turn on LED
  A->>L: Issac to Kelton<br/>Rolecall
  L->>L: Turn on LED
  L->>S: Issac to Kelton<br/>Rolecall
  S->>S: Turn on LED
  S->>K: Issac to Kelton<br/>Rolecall
  K->>K: Turn on LED,<br/> Trash Message
  

  loop
    H->>A: Hafsa to Isaac<br/>Speed is 3m/s
    A->>L: Hafsa to Isaac<br/>Speed is 3m/s
    L->>S: Hafsa to Isaac<br/>Speed is 3m/s
    S->>K: Hafsa to Isaac<br/>Speed is 3m/s
    K->>N: Hafsa to Isaac<br/>Speed is 3m/s
    N->>M: Hafsa to Isaac<br/>Speed is 3m/s
    M->>I: Hafsa to Isaac<br/>Speed is 3m/s
    I->>I: Display "Speed = 3m/s"<br/>on OLED screen, Trash Message

    S->>K: Seth to Isaac<br/>Distance is 4.54m
    K->>N: Seth to Isaac<br/>Distance is 4.54m
    N->>M: Seth to Isaac<br/>Distance is 4.54m
    M->>I: Seth to Isaac<br/>Distance is 4.54m
    I->>I: Display "Distance = 4.54m"<br/>on OLED screen, Trash Message

    K->>N: Kelton to Isaac<br/>Temperature is 23C
    N->>M: Kelton to Isaac<br/>Temperature is 23C
    M->>I: Kelton to Isaac<br/>Temperature is 23C
    I->>I: Display "Temperature = 23C"<br/>on OLED screen, Trash Message

    H->>H: Collect Angular Momentum Data, Calculate
    H->>A: Stabilize Arm<br>Camera to 3 degrees
    A->>A: Adjust Camera Servo to<br/>3 degrees, Trash Message
    
  end
```

## Message Types
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

## Message Types data structures

Message type 1:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Angle |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | A | E |1 | 0 |
| Max Value | A | E | 1| 255|
| Example | A | E |1 | 125 | 

Message type 2:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Throttle |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | A | D |2 | 0 |
| Max Value | A | D | 2| 255|
| Example | A | D |2 | 125 | 

Message type 3:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|**Byte 5**|
| :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Yaw | Pitch |
| Variable Type | char | char | uint8_t | uint8_t | uint8_t |
| Min Value | A | G |5 | 0 | 0 |
| Max Value | A | G | 5| 255| 255 |
| Example | A | G |5 | 125 | 90 |

Message type 4:

||**Byte 1** |**Byte 2**|**Byte 3**|
| :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type |
| Variable Type | char | char | uint8_t |
| Min Value | A | F |4 |
| Max Value | A | F | 4|
| Example | A | F |4 |


Message type 5:

||**Byte 1** |**Byte 2**|**Byte 3**|**Byte 4**|
| :-------: | :-------: | :-------: | :-------: | :-------: |
| Variable Name | Sender_ID | Reciever_ID | Message_Type | Speed |
| Variable Type | char | char | uint8_t | uint8_t |
| Min Value | H | A |5 | 0 |
| Max Value | H | A | 5| 255|
| Example | H | A |5 | 125 | 

Message type 6:

|**Byte 1 (uint8_t)**|**Byte 2-3 (uint16_t)**|
| ------- | ------- |
| 6 | Distance(uint16_t) |

Message type 7:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 7 | Temperature(uint8_t) |



Message type 8:

|**Byte 1 (uint8_t)**|
| ------- |
| 8 |

Message type 9:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|**Byte 3 (uint8_t)**|**Byte 4 (uint8_t)**|**Byte 5 (uint8_t)**|
| ------- | ------- | ------- | ------- | ------- |
| 9 | Relayed sender ID(uint8_t) | Relayed reciever ID(uint8_t) | Relayed message data(uint8_t) |

Message type 10:

|**Byte 1 (uint8_t)**|
| ------- |
| 10 |

Message type 11:

|**Byte 1 (uint8_t)**|
| ------- |
| 11 |
