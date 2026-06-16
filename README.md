# Robotic-Arm
I created a 5 DOF robotic arm from scratch using MG996R and SG90 servo motor which can be controlled by web.
<img width="960" height="1200" alt="WhatsApp Image 2026-05-05 at 11 09 42 PM" src="https://github.com/user-attachments/assets/3d82b132-a272-4160-8036-f86d061723c0" />
# Working Principle

This project controls an MG996R servo motor using an Arduino microcontroller. The Arduino generates PWM (Pulse Width Modulation) signals that determine the angular position of the servo motor.

# How It Works

1. The Arduino initializes communication with the servo using the Servo library.
2. A PWM signal is sent through the designated signal pin.
3. The pulse width corresponds to a specific angle:

   * 0° position → approximately 1 ms pulse
   * 90° position → approximately 1.5 ms pulse
   * 180° position → approximately 2 ms pulse
4. The MG996R servo's internal controller interprets the PWM signal and rotates the shaft to the requested position.
5. The servo continuously receives position commands from the Arduino and adjusts its angle accordingly.

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
