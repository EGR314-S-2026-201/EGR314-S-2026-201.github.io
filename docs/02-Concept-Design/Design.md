---
title: Concept Generation and Design Ideation
---

## Overview
**In a basic paragraph, what is the goal for our exploration device?** 

Keep in mind we have to have at least 1 sensor, 1 actuator, 1 human-machine interface and 1 bidirectional internet communication subsystem and the other 4 subsystems must fit into one of the above categories.

We will build an exploration rover that will be used for exploring environments typically recognized as dangerous for humans. The rover will explore water and/or land based environments and have a chassis with multiple motors to act as actuators for moving a basic chassis around the environment. The human-machine interface will act as a central controller for the chassis and modular subsystems which can be swapped out to meet parameters for missions of different natures.

**In a basic paragraph, who is our audience?**

Our audience are the corporations who use expendable drones/rovers in potentially hostile and unsafe environments. These groups will not be limited to missions of a single unique nature, but rather missions whose parameters can change significantly.


## Design Concepts

### Design Concept 1: Firefighter rover
![FireBot](files/FireRover.jpg)
Full resolution pdf: ![FireBot](files/FireRover.pdf)

**Description:**
This is a firefighting robot, it's purpose is to navigate into dangerous areas and provide fire suppression. The device is equipped with a swiveling nozzle, belt driven locomotion, a 360 camera for navigation, a siren, and 2 auxiliary water tanks. In addition, the electronics box mounted near the back of the rover contains several useful sensors such as temperature, smoke, remaining water pressure, and carbon monoxide. The tanks are refilled and pressurized via a firehose through a connection point in the back of the rover, the rover can also operate using water directly from the hose for an unlimited water supply.

The controller for the rover will have a screen displaying sensor data, and the camera view. The rover's movement, nozzle swivel, and dispensing can all be controlled remotely through the controller via two-way wireless communication between two esp32 boards. The display will also alert the user of dangerously high temperatures or low water pressure with visual and audio cues.

The controller setup will be two joysticks, one for steering, and one for the nozzle swivel. There will be several switches, such as an alarm toggle, nozzle toggle, and switching between internal and external water supplies. Ideally these controls will be kept simplistic to allow users to operate the device without much instruction.

Functionality will be split between 4 groups of 2. A group for designing the drive train, a group for designing the controls and communication protocol, a group for designing the main electronics box, and a group focused on the water nozzle and dispensing system.
