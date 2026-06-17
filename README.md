# Robotic-Arm
I created a 5 DOF robotic arm from scratch using MG996R and SG90 servo motor which can be controlled by web.
<img width="960" height="1200" alt="WhatsApp Image 2026-05-05 at 11 09 42 PM" src="https://github.com/user-attachments/assets/3d82b132-a272-4160-8036-f86d061723c0" />
# Working Principle

This project controls an MG996R servo motor using an Arduino microcontroller. The Arduino generates PWM (Pulse Width Modulation) signals that determine the angular position of the servo motor.

# How It Works

The robotic arm is controlled through a web-based dashboard that communicates with an Arduino Uno in real time.

# System Architecture

```
Web Dashboard
      ↓
Node.js Server
      ↓
Serial Communication (USB)
      ↓
Arduino Uno
      ↓
PCA9685 Servo Driver
      ↓
Servos (Gripper, Wrist, Elbow, Shoulder, Base)
```

# Workflow

# 1. User Input

The user controls the robotic arm using sliders on the web dashboard. Each slider corresponds to a specific joint:

* Gripper
* Wrist
* Elbow
* Shoulder
* Base

### 2. Web Application

The dashboard captures slider values and sends them to a Node.js backend using HTTP requests.

Example:

```json
{
  "angles": [30, 90, 120, 180, 90]
}
```

### 3. Node.js Backend

The backend receives the joint values and converts them into a serial command that can be understood by the Arduino.

Example:

```
M,30,90,120,180,90
```

### 4. Arduino Processing

The Arduino continuously listens for incoming serial commands.

When a command is received:

* Joint values are extracted.
* Values are validated and constrained to safe operating limits.
* Appropriate PWM signals are generated.

### 5. Servo Control

The PCA9685 PWM driver generates precise control signals for each servo.

Joint configuration:

| Channel | Joint    | Type                    |
| ------- | -------- | ----------------------- |
| CH0     | Gripper  | SG90 Positional Servo   |
| CH1     | Wrist    | MG996R Continuous Servo |
| CH2     | Elbow    | MG996R Positional Servo |
| CH3     | Shoulder | TD-8120MG 360° Servo    |
| CH4     | Base     | MG996R Continuous Servo |

### 6. Joint Movement

#### Positional Servos

The Gripper, Elbow, and Shoulder move to a specific target angle based on the slider position.

# Continuous Rotation Servos

The Wrist and Base use speed control:

* 90 = Stop
* Less than 90 = Rotate in one direction
* Greater than 90 = Rotate in the opposite direction

## Features

* Real-time browser-based control
* Responsive web dashboard
* USB serial communication
* 5 Degrees of Freedom (5-DOF)
* Support for both positional and continuous rotation servos
* Custom servo calibration
* Home and preset positions

## Future Improvements

* Inverse Kinematics
* Motion Planning
* Trajectory Generation
* Position Feedback Sensors
* 3D Visualization
* Wireless Control
* Computer Vision Integration

# Hardware Requirements

1. Arduino Uno/ Nano (or any other programming board)
2. One 20KG servo motor (shoulder joint)
3. Three MG996R servos (Base, Elbow and Wrist)
4. One SG90 servo (Gripper)
5. A servo driver PCA9685
6. A power supply lipo or lion

# Arm Model

I 3d printed a design i got from the web here's the link for it
https://www.printables.com/model/818975-compact-robot-arm-arduino-3d-printed
