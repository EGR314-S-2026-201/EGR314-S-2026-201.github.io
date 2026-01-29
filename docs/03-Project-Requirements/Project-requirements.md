---
title: Project Requirements
---

## Requirements Table
For organizational purposes, our group decided to split into several sub-teams to divide the tasks between.

**201A:** Wifi and Human interface, Neel Garde and Isaac Smith

**201B:** Movement and Propulsion, Jacob Andrus and K Phang

**201C:** Camera and positioning arm, Austin Gonzalez and Levi Addink

**201D:** Research and Development, Seth Merwin and Kelton Jensen


|**Requirement Description**|**Measure of Threshold**|**Target Measure**|**Stretch Requirement (Y-N)**|**Assignee(s)**|**Satisfied Feature**|
| :------- | :------- | :------- |:------- |:------- |:------- |
| All microcontrollers use the same daisy-chain UART communication setup | 8 out 8 team microcontrollers | 8 out 8 team microcontrollers | N | All | Project requirement |
| 1 microcontroller is assigned to each of the 8 individual subsystems | 8 out 8 team microcontrollers | 8 out 8 team microcontrollers | N | All | Project requirement |
| At least one PIC and one ESP32 is used | 2 out of 2 subsystems | 2 out of 2 subsystems | N | All | Project requirement |
| Wireless or internet communication | Able to send or receive data wirelessly or interface with an internet protocol | Able to send or receive data wirelessly or interface with an internet protocol | N | Team 201A | Antenna to receive signals from a remote (Types of modules) |
| The robot can be remotely controlled (wired or wirelessly) via a dedicated human interface device | Functional screen and buttons | Functional screen and buttons on a physically separate subsystem | N | Team 201A | Project Requirement |
| The device will be capable of aquatic movement | Capable of controlling at least two motors | Capable of controlling at least two motors with propellers and a rudder | N | Team 201B | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The device will be battery-powered | Subsystems can take power from an unregulated source within 3.3-12V | Subsystems are powered by a battery unit | N | Team 201A | Antenna to receive signals from a remote (Types of modules) |
| The robot is capable of optical inspection | Some form of photoresistive or lidar sensor is used | An optical camera is used | N | Team 201C | LiDAR scanning (Types of modules) / Camera to record images around the rover (User interface and interaction) |
| The controller interface is familiar and intuitive to the operator | Easily understood buttons and text are used | The controller is something familiar to most people (Xbox, PS5, N64 etc.) | Y | Team 201A | Project Requirement |
| The robot can change movement mechanism through a direct mount modular interface without adapters | Direct attachment achieved with no intermediary hardware | Direct attachment achieved quickly with no intermediary hardware | N | Team 201B | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The robot should have directional steering | Able to move a steering mechanism to change the direction of the robot without changing the power of the drive/propulsion motors | The robot will have electronic power steering | N | Team 201B | Bidirectional motor movement (Types of modules) |
| The robot should have backwards and forward propulsion | The driving motors should be able to change direction | The driving motors should be able to change direction of rotation | N | Team 201B | Bidirectional motor movement (Types of modules) |
| The robot should be able to move both motors independently | The driving motors should have their own independent controls  | Driving motors can change directions and speed independently | Y | Team 201B | Bidirectional motor movement (Types of modules) |
| The robot shall use the same communication procedures to control all mobility configurations | Number of unique communication protocols or control mappings required across mobility modules | All mobility configurations operate using one identical communication protocol and control mapping | N | All | Parts can be swapped to allow movement over different types of terrain (Exploration) |
| The robot will have a distance sensing capabilities | Distance sensors of some sort are used, Lidar, ultrasonic etc | Lidar sensor is used | N | Team 201D | LiDAR scanning (Types of modules) |
| The robot will be able to measure temperature | Temperature sensor will be able to measure the ambient temperature | The sensor should be able to show how hot or cold the water is | N |  Team 201D | Temperature sensor(Types of modules) |


## Requirements from features

**"Project requirement"**:
This project has certain requirements that we must complete, these requirements can be found [here](https://embedded-systems-design.bitbucket.io/314/project-description/) on the project description page.

**"Antenna to receive signals from a remote"**:
To have an antenna and remote our device has to be wireless, this creates a few requirements such as the need for a wireless communication protocol, and a battery power supply.

**"Camera to record images around the rover"**:
In this case the feature is the requirement. We want a camera on the device, so we need to have a camera and a board to control it.

**"Parts can be swapped to allow movement over different types of terrain"**:
To allow the body of the device to be swapped, it must be designed with this capability in mind. Our team decided we would like to make this process simple, and this led to the requirement of a connection with no intermediary hardware. Additionally the device will have to communicate with several chassis types, which led to the requirement that all mobility configurations should have the same communication procedures.

**"LiDAR scanning"**:
The feature LiDAR scanning led to the requirement of having some sort of distance detection device. Although we added a minimum goal of having any sort of distance sensor, the ideal is LiDAR.

**"Bidirectional motor movement"**
To have bidirectional motor movement our device needs to be able to have backwards and forward propulsion, and independent motor control. Our team decided to make independent motor control a stretch goal, and add the requirement of directional steering. This should be able to accomplish the same function as bidirectional motor control, while ensuring the goal is achievable.

**"Temperature Sensor"**:
The feature of having a temperature sensor, requires having a temperature sensor. That is all.
