# LED Detection with ESP32-CAM and OpenCV

## Project Overview
This project provides the software for a drone-based LED detection system. It consists of an Arduino sketch for the ESP32-CAM to stream video and a Python script with OpenCV to process that video for color detection. The processing is handled on a ground-based computer to minimize payload and power draw on the drone.

## Requirements

### Hardware
*   **ESP32-CAM Module (AI-Thinker):** Already mounted on the drone.
*   **Computer:** For running the Python scripts.
*   **Wi-Fi Network:** To establish communication.

### Software
*   **Arduino IDE:** For flashing the ESP32-CAM.
*   **Python 3:** The programming language for the ground station script.
*   **Libraries:**
    ```sh
    pip install opencv-python numpy
    ```

## Installation and Usage

### Step 1: Flash the ESP32-CAM
1.  **Open Arduino IDE:** Make sure the ESP32 board support and `ESP32-CAM` libraries are installed.
2.  **Upload `CameraWebServer`:** Open the example sketch and update the Wi-Fi SSID and password.
3.  **Flash the Module:** Connect the ESP32-CAM via an FTDI programmer and upload the sketch.
4.  **Get IP Address:** Use the Serial Monitor to find the IP address of your ESP32-CAM. The video stream will be at `http://<ESP32_IP_ADDRESS>:81/stream`.

### Step 2: Calibrate HSV Thresholds
Before running the main detection script, you must find the correct color ranges for the LEDs under your specific operating conditions.

1.  **Update Stream URL:** In the `hsv_calibration.py` script, replace the placeholder `esp32_cam_url` with your ESP32-CAM's IP address.
2.  **Run Calibration:** Execute the script from your terminal:
    ```sh
    python hsv_calibration.py
    ```
3.  **Adjust Trackbars:** An interface with trackbars will appear. Tune the `H_min`, `H_max`, `S_min`, `S_max`, `V_min`, and `V_max` values until the LED appears as a solid white blob in the "Masked Feed" window.
4.  **Record Values:** Press `q` to quit, and the final HSV ranges will be printed to the console. Copy these values.

### Step 3: Run the LED Detection Script
1.  **Update IP Address:** In `led_detection.py`, update the `esp32_cam_url`.
2.  **Update HSV Ranges:** Replace the placeholder `color_ranges` dictionary with the values you obtained during calibration.
3.  **Execute Detection:** Run the main script:
    ```sh
    python led_detection.py
    ```
4.  **Observe:** A window will display the live video feed with bounding boxes and color labels around the detected LEDs.

## Scripts
*   **`hsv_calibration.py`:** Used for interactive calibration of HSV ranges.
*   **`led_detection.py`:** The main script for real-time LED color detection.

## Troubleshooting
*   **Poor Detection:** If the script fails to detect colors accurately, re-run the calibration script.
*   **Stream Issues:** Ensure a stable Wi-Fi connection. Adjust the ESP32-CAM's resolution or framerate in the Arduino sketch if the video stream is laggy.
*   **Noise:** Use morphological operations (e.g., `cv2.erode`, `cv2.dilate`) to clean up the mask and remove false positives.

## Contributing
Feel free to open an issue or submit a pull request to improve this project.

