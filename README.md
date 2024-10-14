# COLOR SENSOR CAR AND LINE FOLLOWING SENSOR

---
## Author: Juan Carlos Gonzalez

## Email: jcgi.laboral@gmail.com

## Date: March 2023

---


## Abstract

This article discusses the development of a small car that, through Arduino, will be able to find specific points indicated via a mobile app connected to Arduino via Bluetooth.

**Keywords**: Car, Arduino, Sensor

## I. Project Objective

Apply the knowledge from Digital Systems and Computational Theory classes to create a car that will locate predetermined points based on a pattern. The mobile application, connected to Arduino via Bluetooth, will send instructions to the car, and it will stop once the point is found, waiting for the next instruction.

## II. Theoretical Framework

### A. Background

Previous projects include a line-following car using Arduino and infrared sensors, which follows a black line on a white background. The sensors output 1 or 0 when they detect or lose the line, instructing the motors to stop or continue. Another project involved a car controlled remotely via the Arduino Bluetooth module, using the mobile app as a remote to control movements.

In terms of color sensors, these typically compare colors based on the three primary colors (red, green, and blue). In a past project, when the sensor detected a specific color, it would light up an LED accordingly.

### B. Logical Circuit Base

The materials used in this project were:

- Arduino Uno
- Car chassis kit
- 2 Infrared Sensors FC-51
- 1 Color Sensor TCS3200
- H-Bridge
- Bluetooth Module HC-6

### C. Circuit Diagrams

Below are the diagrams for each component used in this project:

- **Figure 1**: Arduino UNO Components
- **Figure 2**: FC-51 Infrared Sensor Diagram
- **Figure 3**: TCS3200 Color Sensor connection to Arduino, with 5 inputs, 2 grounds, and 1 voltage
- **Figure 4**: Diagram showing the connection of the L293D H-Bridge for controlling the two motors
- **Figure 5**: HC-6 Bluetooth Module and its connection diagram

## III. Experimental Framework

This section details the experimental process followed during the project.

### A. Logical Operation Description

The project operates primarily via an Arduino Uno board, which is programmed to interpret Bluetooth signals. These signals instruct the car on where to go. The Arduino processes these signals and, with the help of the equipped sensors, moves the car from one point to another.

The car starts in an initial state based on a fabric with the following pattern:

- **Figure 7**: Car Pattern

Once the initial state of the car is defined, the mobile app in "Terminal Mode" sends a command via Bluetooth, telling the car which point to move to. The Arduino program verifies the commands and moves according to predefined patterns.

- **Figure 9**: Arduino Mobile App Terminal Mode and Bluetooth Module

The points have colored edges, which the car uses to determine the path. For example, if the car is in the initial state (q0) and needs to move to q4, it will rotate to detect the green strip (Figure 7), then follow the black line using the infrared sensors to reach q4.

All possible paths between the points are predefined in the Arduino program.

### B. State Diagram

The state diagram for the car is shown below.

### C. Grammar and Derivation

This project also involves using grammar to derive the transitions between points.

## IV. Project Operation

### A. User Manual

1. To test the project, install the Arduino Bluetooth app on your mobile device and connect to the car's Bluetooth module.
   
- **Figure 10**: Connection screen between the device and module

2. Once connected, select "Terminal Mode" on the main screen (Figure 10). In this mode, type the point where you want the car to go. In the example, the car starts at point q0 (the initial state) and moves to point q4.

3. After hitting enter, the car will rotate to find the path to its destination.

- **Figure 11**: The car begins rotating, searching for the green path that leads to point 4 (Figure 8).

4. After the car detects the assigned color, it will follow the black line using the infrared sensors until it reaches the destination.

5. To send a new command, repeat step 2, and the car will search for the new path to the destination.

### B. Detailed Programming

The program was developed using the Arduino IDE. We first defined the pins for the Bluetooth module inputs and outputs. Then, we declared a class to assign transitions between points. Paths between points are defined as arrays, each identified by the color to follow. Sensor inputs and outputs are declared, and variables for input/output states are initialized in the `setup` function.

The `leer_cadenas` function validates the command received in "Terminal Mode." The automaton starts if the command is valid.

### Functions:

- States of the automaton
- Final state of the automaton defining the destination
- Functions to handle transitions and line-following
- Functions to identify colors using the color sensor

## V. Results and Conclusions

Throughout the project, obtaining materials was challenging due to their cost and limited availability. Understanding how each sensor worked and learning Arduino programming also took considerable time. Initially, the programming was faulty, and the motors did not work. After debugging, we realized that the issue was insufficient voltage to the motors. Ensuring that each motor receives at least 4.5 volts is essential for correct operation.

## References

- [TCS3200 Color Sensor with Arduino](https://hetpro-store.com/TUTORIALES/sensor-de-color-tcs3200-con-arduino/)
- [Arduino Line Following Robot Kit](https://www.taloselectronics.com/kit-robot-seguidor-de-linea-para-arduino/)
- [Build a Line Following Robot with Arduino](https://jhosman.com/index.php/2013/06/04/construir-un-robot-seguidor-de-linea-con-arduino-software-libre-hardware-libre/)
