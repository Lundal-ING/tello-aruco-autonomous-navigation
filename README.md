
# Autonomous Tello Drone Navigation Using ArUco Markers

Autonomous indoor drone navigation using Python, OpenCV, and ArUco markers for real-time visual pose estimation, target detection, and GPS-independent navigation.

## Project Overview

This project explores autonomous indoor navigation using a Ryze Tello quadcopter equipped with an onboard camera. The goal was to develop a vision-based navigation system capable of detecting ArUco markers, estimating their relative positions, and autonomously navigating toward a selected target without relying on GPS or external positioning systems.

The system was developed in Python using OpenCV for computer vision, NumPy for numerical calculations, and Matplotlib for 3D visualization.

## Key Features

- **ArUco Marker Detection:** Detects and identifies visual markers using OpenCV.
- **Camera Calibration:** Estimates intrinsic camera parameters and lens distortion coefficients.
- **Real-Time Pose Estimation:** Calculates the relative position and orientation of detected markers.
- **Autonomous Target Selection:** Performs a 360° scan and selects the nearest detected marker.
- **Autonomous Navigation:** Navigates toward the selected marker and attempts to land at a predefined distance of 0.5 metres.
- **3D Visualization:** Visualizes detected marker positions and orientations relative to the camera.

## Technologies Used

| Technology | Application |
|------------|-------------|
| Python | Main programming language |
| OpenCV | Image processing and ArUco detection |
| NumPy | Matrix operations and coordinate transformations |
| Matplotlib | 3D pose visualization |
| Tello SDK | Drone communication and control |
| UDP | Wireless communication with the drone |
| Ryze Tello | Quadcopter hardware platform |

## System Architecture

The autonomous navigation system follows this workflow:

1. **Takeoff:** The drone takes off and stabilizes.
2. **Marker Detection:** The camera captures images and identifies visible ArUco markers.
3. **Pose Estimation:** The system estimates the relative position and orientation of each detected marker.
4. **3D Visualization:** Detected marker poses are visualized in a three-dimensional coordinate system.
5. **Environment Scanning:** The drone performs a 360° rotation in 20° increments to detect additional markers.
6. **Target Selection:** The nearest detected marker is selected.
7. **Autonomous Movement:** The drone rotates toward the selected marker and moves to approximately 0.5 metres from it.
8. **Landing:** The drone performs an autonomous landing.

## Project Structure

```text
tello-aruco-autonomous-navigation/
│
├── main.py
├── ArUco_tagg.py
├── pose_tools.py
├── Visualize.py
├── kamera_kalibrering.py
├── requirements.txt
└── README.md
```

### Python Modules

**main.py**

Main control program responsible for communication with the Tello drone, video streaming, marker searching, target selection, navigation, and landing.

**ArUco_tagg.py**

Detects ArUco markers and estimates their relative position and orientation using OpenCV.

**pose_tools.py**

Processes marker pose information and converts coordinate transformations for visualization.

**Visualize.py**

Generates 3D visualizations of detected markers and their coordinate systems using Matplotlib.

**kamera_kalibrering.py**

Performs camera calibration using a chessboard pattern to estimate the camera matrix and lens distortion coefficients.

## Installation

### Requirements

- Python 3
- Ryze Tello drone
- Computer with Wi-Fi connectivity
- Printed ArUco markers

Install the Python dependencies:

```bash
pip install -r requirements.txt
```

### Running the Program

1. Connect your computer to the Tello drone's Wi-Fi network.
2. Ensure that the drone is sufficiently charged and placed in a safe indoor environment.
3. Configure the camera calibration parameters and check the relevant file paths.
4. Start the main program:

```bash
python main.py
```

The application communicates with the drone through UDP and uses the onboard camera for visual feedback.

**Note:** The code was reconstructed from the original project report and has not been retested on the physical drone. The camera calibration script also requires a NumPy import correction before use. Additional configuration may be necessary depending on the environment and installed OpenCV version.

## Experimental Results

The system was developed and tested at the ARIS Robotics Laboratory at OsloMet.

During testing, the drone successfully detected ArUco markers, estimated their relative poses, selected the nearest marker, and performed autonomous navigation based on visual information.

The target landing distance was **500 mm** from the selected marker.

| Test | Measured Distance |
|------|-------------------|
| 1 | 500 mm |
| 2 | 470 mm |
| 3 | 600 mm |
| 4 | 460 mm |
| 5 | 510 mm |
| **Average** | **508 mm** |

Although the average landing distance was close to the target, individual tests showed noticeable variation. The drone also experienced lateral positioning errors.

### Limitations

- Airflow and indoor ventilation affected the drone's stability.
- Positioning accuracy decreased during landing.
- The drone occasionally experienced lateral drift.
- Rotation inaccuracies could cause markers to move outside the camera's field of view.
- Further improvements could include sensor fusion, feedback-based position correction, and more advanced control algorithms.

## Learning Outcomes

The project provided practical experience in:

- Computer vision and real-time image processing
- Camera calibration and pose estimation
- Autonomous robotic navigation
- Coordinate transformations and 3D visualization
- Python programming and hardware-software integration
- Experimental testing and analysis of positioning errors
- Collaborative engineering development

## Project Team

Developed as a group project 

This repository presents the original student project's Python implementation for educational and portfolio purposes.
