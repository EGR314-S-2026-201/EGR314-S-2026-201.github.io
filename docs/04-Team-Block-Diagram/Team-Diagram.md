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

  loop
    I->>M: Isaac to Hafsa<br/>Get Speed
    M->>N: Isaac to Hafsa<br/>Get Speed
    N->>J: Isaac to Hafsa<br/>Get Speed
    J->>P: Isaac to Hafsa<br/>Get Speed
    P->>H: Isaac to Hafsa<br/>Get Speed
    H->>H: Collect Acceleration Data,<br/>Calculate, Trash Message
    H->>A: Hafsa to Isaac<br/>Speed is 3m/s
    A->>L: Hafsa to Isaac<br/>Speed is 3m/s
    L->>S: Hafsa to Isaac<br/>Speed is 3m/s
    S->>K: Hafsa to Isaac<br/>Speed is 3m/s
    K->>N: Hafsa to Isaac<br/>Speed is 3m/s
    N->>M: Hafsa to Isaac<br/>Speed is 3m/s
    M->>I: Hafsa to Isaac<br/>Speed is 3m/s
    I->>I: Display "Speed = 3m/s"<br/>on OLED screen

    I->>M: Isaac to Seth<br/>Get Distance
    M->>N: Isaac to Seth<br/>Get Distance
    N->>J: Isaac to Seth<br/>Get Distance
    J->>P: Isaac to Seth<br/>Get Distance
    P->>H: Isaac to Seth<br/>Get Distance
    H->>A: Isaac to Seth<br/>Get Distance
    A->>L: Isaac to Seth<br/>Get Distance
    L->>S: Isaac to Seth<br/>Get Distance
    S->>S: Collect Distance Data,<br/>Trash Message
    S->>K: Seth to Isaac<br/>Distance is 4.54m
    K->>N: Seth to Isaac<br/>Distance is 4.54m
    N->>M: Seth to Isaac<br/>Distance is 4.54m
    M->>I: Seth to Isaac<br/>Distance is 4.54m
    I->>I: Display "Distance = 4.54m"<br/>on OLED screen

    I->>M: Isaac to Kelton<br/>Get Temperature
    M->>N: Isaac to Kelton<br/>Get Temperature
    N->>J: Isaac to Kelton<br/>Get Temperature
    J->>P: Isaac to Kelton<br/>Get Temperature
    P->>H: Isaac to Kelton<br/>Get Temperature
    H->>A: Isaac to Kelton<br/>Get Temperature
    A->>L: Isaac to Kelton<br/>Get Temperature
    L->>S: Isaac to Kelton<br/>Get Temperature
    S->>K: Isaac to Kelton<br/>Get Temperature
    K->>K: Collect Temperature Data,<br/>Trash Message
    K->>N: Kelton to Isaac<br/>Temperature is 23C
    N->>M: Kelton to Isaac<br/>Temperature is 23C
    M->>I: Kelton to Isaac<br/>Temperature is 23C
    I->>I: Display "Temperature = 23C"<br/>on OLED screen

    H->>H: Collect Angular Momentum Data, Calculate
    H->>A: Stabilize Arm<br>Camera to 3 degrees
    A->>A: Adjust Camera Servo to<br/>3 degrees, Trash Message
  end
```

## Message Types
| **message type byte 1 (uint8_t)** | **description** |
| -------: | :------- |
| 1  | Set steering angle in degrees |
| 2  | Set steering throttle percentage |
| 3  | Set camera angle in degrees |
| 4  | Take picture |
| 5  | Get speed data |
| 6  | Get distance data |
| 7  | Get temperature data |
| 8  | Display speed data |
| 9  | Display distance data |
| 10 | Display temperature data |
| 11 | Adjust camera angle in degrees |

## Message Types data structures

Message type 1:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 1 | Angle(uint8_t) |

Message type 2:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 2 | Throttle(uint8_t) |

Message type 3:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 3 | Angle(uint8_t) |

Message type 4:

|**Byte 1 (uint8_t)**|
| ------- |
| 4 |


Message type 5:

|**Byte 1 (uint8_t)**|
| ------- |
| 5 |

Message type 6:

|**Byte 1 (uint8_t)**|
| ------- |
| 6 |

Message type 7:

|**Byte 1 (uint8_t)**|
| ------- |
| 7 |

Message type 8:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 8 | Speed(uint8_t) |

Message type 9:

|**Byte 1-2 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 9 | Distance(uint8_t) |

Message type 10:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 10 | Temperature(uint8_t) |

Message type 11:

|**Byte 1 (uint8_t)**|**Byte 2 (uint8_t)**|
| ------- | ------- |
| 11 | Angle(uint8_t) |
