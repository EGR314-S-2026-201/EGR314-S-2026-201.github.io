---
title: Project Requirements
---

## Requirements Table

|**Requirement Description**|**Measure of Threshold**|**Target Measure**|**Stretch Requirement (Y-N)**|**Assignee(s)**|**Satisfied Feature**|
| :------- | :------- | :------- |:------- |:------- |:------- |
| All microcontrollers use the same daisy-chain UART communication setup | 8/8 | 8/8 | N | All | Project requirement |
| 1 microcontroller is assigned to each of the 8 individual subsystems | 8/8 | 8/8 | N | All | Project requirement |
| At least one PIC and one ESP32 is used | 2/2 | 2/2 | N | ESP32: \nPIC: | Project requirement |
| Wireless or internet communication | Able to send or receive data wirelessly or interface with an internet protocol | Able to send or receive data wirelessly or interface with an internet protocol | N |  | Antenna to receive signals from a remote (Types of modules) |
| The robot can be remotely controlled (wired or wirelessly) via a dedicated human interface device | Functional screen and buttons | Functional screen and buttons on a physically separate subsystem | N |  | Project Requirement |
| The device will be capable of aquatic movement | Capable of controlling at least two motors | Capable of controlling at least two motors with propellers and a rudder | N |  |  |
| The device will be battery-powered | Subsystems can take power from an unregulated source within 3.3-12V | Subsystems are powered by a battery unit | N |  | Antenna to receive signals from a remote (Types of modules), device must be battery-powered to be wireless |
| The robot is capable of optical inspection | Some form of photoresistive or lidar sensor is used | An optical camera is used | Y |  | LiDAR scanning (Types of modules) / Camera to record images around the rover (User interface and interaction) |
| The controller interface is familiar and intuitive to the operator | Easily understood buttons and text are used | The controller is a GuitarHero guitar | Y |  | Guitar Hero controller (robot interface or input concept) |
