---
title: Block Diagram, Protocol, and Message Structure
---

## Header

## Message Types
|**message type
byte 1-2
(uint16_t)**|**description**|
| -------: | :------- |
| 1 | Set steering angle in degrees |
| 2 | Set steering throttle percentage |
| 3 | Set camera angle in degrees |
| 4 | Take picture |
| 5 | Get distance data |
| 6 | Get temperature data |
| 7 | Display distance data |
| 8 | Display temperature data |

## Message Types data structures

Message type 1:

(Example empty table)
|**Byte 1-2 (uint16_t)**|**Other stuff**|
| 12 | X(uint8_t) |
