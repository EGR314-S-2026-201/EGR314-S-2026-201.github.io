---
title: Project Requirements
---

## Requirements Table
For orginizational purposes, our group decided to split into several sub-teams to divide the tasks between.
201A: Wifi and Human interface, Neel Garde and Isaac Smith
201B: Movement and Propulsion, Jacob Andrus and K Phang
201C: Camera and positioning arm, Austin Gonzalez and Levi Addink
201D: Research and Development, Seth Merwin and Kelton Jensen

|**Requirement Description**|**Measure of Threshold**|**Target Measure**|**Stretch Requirement (Y-N)**|**Assignee(s)**|**Satisfied Feature**|
| :------- | :------- | :------- |:------- |:------- |:------- |
| All microcontrollers use the same daisy-chain UART communication setup | 8 out 8 team microcontrollers | 8 out 8 team microcontrollers | N | All | Project requirement |
| 1 microcontroller is assigned to each of the 8 individual subsystems | 8 out 8 team microcontrollers | 8 out 8 team microcontrollers | N | All | Project requirement |
| At least one PIC and one ESP32 is used | 2 out of 2 subsystems | 2 out of 2 subsystems | N | ESP32: \nPIC: | Project requirement |
| Wireless or internet communication | Able to send or receive data wirelessly or interface with an internet protocol | Able to send or receive data wirelessly or interface with an internet protocol | N | Team 201A | Antenna to receive signals from a remote (Types of modules) |
| The robot can be remotely controlled (wired or wirelessly) via a dedicated human interface device | Functional screen and buttons | Functional screen and buttons on a physically separate subsystem | N | Team 201A | Project Requirement |
| The device will be capable of aquatic movement | Capable of controlling at least two motors | Capable of controlling at least two motors with propellers and a rudder | N | Team201B | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The device will be battery-powered | Subsystems can take power from an unregulated source within 3.3-12V | Subsystems are powered by a battery unit | N | Team 201A | Antenna to receive signals from a remote (Types of modules) |
| The robot is capable of optical inspection | Some form of photoresistive or lidar sensor is used | An optical camera is used | N | Team 201C | LiDAR scanning (Types of modules) / Camera to record images around the rover (User interface and interaction) |
| The controller interface is familiar and intuitive to the operator | Easily understood buttons and text are used | The controller is a GuitarHero guitar | Y |  | Guitar Hero controller (robot interface or input concept) |
| The robot can change movement mechanism through a direct mount modular interface without adapters | Direct attachment achieved with no intermediary hardware | Direct attachment achieved quickly with no intermediary hardware | N | 201B | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The robot should have directional steering | Able to move a steering mechanism to change the direction of the robot without changing the power of the drive/propulsion motors | The robot will have electronic power steering | N | 201B | Bidirectional motor movement (Types of modules) |
| The robot should have backwards and forward propulsion | The driving motors should be able to change direction | The driving motors should be able to change direction of rotation | N | 201B | Bidirectional motor movement (Types of modules) |
| The robot should be able to move both motors independently | The driving motors should have their own independent controls  | Driving motors can change directions and speed independently | Y | 201B | Bidirectional motor movement (Types of modules) |
| The robot shall use the same communication procedures to control all mobility configurations | Number of unique communication protocols or control mappings required across mobility modules | All mobility configurations operate using one identical communication protocol and control mapping | | All | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The robot will have a distance sensing capabilities | Distance sensors of some sort are used, Lidar, ultrasonic etc | Lidar sensor is used | N | 201D | LiDAR scanning (Types of modules) |
