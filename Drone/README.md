# Drone Build for LED Detection Project

## Project Overview
This document details the hardware components and assembly process for the drone platform used in the LED detection project. The drone is designed to be lightweight and features an ESP32-CAM module for streaming video of LED targets. The assembly focuses on a robust, functional build that can be easily maintained and adapted.

## Requirements

### Hardware
*   **ESP32-CAM Module:** The specific module used for this project is the AI-Thinker version.
*   **Drone Frame:** A lightweight, sturdy quadcopter frame. This can be an off-the-shelf kit or a 3D-printed custom design.
*   **Flight Controller (FC):** A standard flight controller with a 5V power output is recommended.
*   **Motors, ESCs, and Propellers:** The choice of motors, electronic speed controllers, and propellers should match the frame size and desired payload capacity.
*   **LiPo Battery:** Powering the drone.
*   **5V BEC (Battery Elimination Circuit):** To step down the LiPo battery voltage to a stable 5V for the ESP32-CAM.
*   **FTDI Programmer:** For flashing the ESP32-CAM with firmware.
*   **3D-Printed Camera Mount:** A secure mount to attach the ESP32-CAM to the drone frame.
*   **Wiring and Connectors:** Assorted jumper wires and JST connectors for internal connections.

### Tools
*   Soldering Iron and Solder
*   Hex Key Set
*   Wire Strippers/Cutters
*   3D Printer (if using a custom mount)

## Assembly Instructions

### Step 1: Frame Assembly
*   Assemble the drone frame according to the manufacturer's instructions.
*   Ensure all screws are secure, but do not overtighten.

### Step 2: Motor and ESC Installation
*   Mount the motors to the frame arms.
*   Solder the motor wires to the ESCs.
*   If necessary, test motor direction and swap any two motor wires to reverse direction.

### Step 3: Flight Controller and BEC Wiring
*   Mount the flight controller to the frame, ensuring the arrow on the FC points forward.
*   Connect the ESCs to the appropriate output ports on the FC.
*   Solder the 5V BEC to the flight controller's power distribution.
*   Wire the ESP32-CAM to the BEC's 5V and GND outputs.

### Step 4: ESP32-CAM Mounting and Flashing
*   Mount the ESP32-CAM module in its 3D-printed enclosure or mount.
*   Connect the FTDI programmer to the ESP32-CAM for the firmware upload. Refer to the `README_LED_DETECTION.md` for software details.
*   Once flashed, mount the ESP32-CAM to the drone frame, ensuring the camera has an unobstructed view.

## Pre-Flight Checks
1.  **Power Test:** Connect the battery and check all connections. Verify that the ESP32-CAM receives power.
2.  **Motor Test:** Power up the motors and ensure they spin correctly and smoothly.
3.  **Stability Check:** Ensure all components are securely mounted and there are no loose wires.

## Troubleshooting
*   **Loss of Wi-Fi Signal:** If the ESP32-CAM loses connection, check for signal interference from other drone components. Consider using an external antenna if necessary.
*   **Power Issues:** If the ESP32-CAM is unstable, use a capacitor on the 5V line to smooth out power spikes, especially if the camera flash is used.
