
---

# Self-Driving Vehicle Project 🚗🤖  
_A Convolutional Neural Network Based Autonomous robot_

## Overview 📝

The **Self-Driving Vehicle** project is an autonomous driving system built on a Raspberry Pi 4, utilizing deep learning for real-time steering control. A Convolutional Neural Network (CNN) processes video input from a camera to predict steering angles, guiding the vehicle autonomously. Image data, captured during manual driving, is used to train the model. The system integrates OpenCV for image processing, TensorFlow/Keras for model training, and GPIO for motor control, enabling the vehicle to drive based on visual input. All computations occur on the Pi, making it a compact, scalable solution for self-driving applications.


## Features 🚀

- **Real-time Image Processing**: Utilizes OpenCV to continuously capture video feed from a camera, analyzing each frame for input data.
- **Joystick-Based Data Collection**: Allows manual control of the vehicle for data collection purposes, enabling the generation of datasets that consist of images and steering angles.
- **Deep Learning Model for Steering**: Trains a Convolutional Neural Network (CNN) model on collected data, enabling the prediction of steering angles based on real-time image input.
- **Autonomous Navigation and Control**: The trained model is deployed for real-time vehicle navigation, leveraging motor control and sensor data to autonomously drive in its environment.
- **Scalable**: The framework is adaptable to different types of vehicles and can be extended to incorporate more complex sensor data such as LiDAR, GPS, etc.
  
## Technology Stack 🧑‍💻

- **Hardware**:
  - **Raspberry Pi 4**: Central computing unit for running the vehicle control system, handling model inference, and interacting with sensors/motors.
  - **USB Webcam**: Captures real-time video feed to provide visual data for the system.
  - **Motor Driver (L298N)**: Controls the vehicle's motors based on signals from the Raspberry Pi.
  - **DC Motors**: Used for vehicle locomotion, controlled via the motor driver.
  - **Joystick Controller**: Used for manual control during data collection phases.
  - **Chassis**: Physical structure that houses the hardware components.

- **Software**:
  - **Python 3**: Core programming language used to implement the vehicle's software system.
  - **OpenCV**: Image processing library for handling video input, frame extraction, and data augmentation.
  - **TensorFlow/Keras**: Machine learning framework used for building, training, and deploying the Convolutional Neural Network (CNN) model.
  - **Numpy**: For numerical computations and handling of array data structures.
  - **Matplotlib**: Data visualization for understanding training results, error rates, and model accuracy.

## Modules Used 🔧

This section describes each of the major modules within the system.

### 1. **Data Collection Module** 📸  
   This module is responsible for capturing video frames from the webcam while simultaneously logging joystick input data (steering angles) to create a training dataset. The dataset comprises images that represent the vehicle’s perspective on the road and corresponding driving decisions.

   - **Input**: Real-time video feed (from webcam) and joystick input.
   - **Output**: Image dataset and a corresponding CSV log of joystick steering angles.

   **Main Script**: `DataCollectionModule.py`

### 2. **Data Preprocessing Module** 🔄  
   This module takes the raw image dataset and performs preprocessing tasks such as resizing, normalization, and data augmentation (e.g., flipping, cropping). Preprocessing ensures that the images are optimized for feeding into a machine learning model.

   - **Input**: Raw image dataset and CSV log.
   - **Output**: Processed images suitable for model training.

   **Main Script**: Integrated within `Training.py`.

### 3. **Model Training Module** 📊  
   This is the core of the machine learning pipeline. It reads the preprocessed data and trains a Convolutional Neural Network (CNN) to predict the steering angle based on visual input from the camera. The model is trained using supervised learning, where the input is an image and the output is a corresponding steering angle.

   - **Input**: Preprocessed images and steering angle labels (from CSV).
   - **Output**: Trained model (`model.h5`).

   **Key Technologies**: TensorFlow, Keras

   **Main Script**: `Training.py`

### 4. **Vehicle Control Module** 🚦  
   This module deploys the trained CNN model to control the vehicle autonomously. It continuously captures video input, uses the CNN model to predict the appropriate steering angle, and sends control signals to the motor driver for real-time actuation of the vehicle’s motors.

   - **Input**: Real-time video from the webcam.
   - **Output**: Motor control signals based on predicted steering angle.

   **Main Script**: `RunMain.py`

## Setup Guide 🛠️

- Raspberry Pi 4 with Raspbian OS installed.
- A USB camera compatible with OpenCV.
- Motor driver and motors compatible with the Raspberry Pi.
- Internet connection for downloading required Python packages.


## 📂 Project Structure

The project is divided into three main phases: **Data Collection**, **Model Training**, and **Implementation**. Below is an overview of the folder and file structure:

```
self-driving-car-project/
│
├── Data-Collection/
│   ├── DataCollectionMain.py     # Main script for managing the data collection process
│   ├── DataCollectionModule.py   # Module responsible for collecting training data (images, sensor data, etc.)
│   ├── JoyStickModule.py         # Interface module for controlling the car using a joystick
│   ├── MotorModule.py            # Controls the car's motor and movement during data collection
│   └── WebcamModule.py           # Handles image capture from the webcam
│
├── Model-Training/
│   ├── Training.py               # Script for training the machine learning model on the collected data
│   ├── requirements.txt          # Python package dependencies for training
│   └── utils.py                  # Utility functions for preprocessing and model training (data augmentation, normalization, etc.)
│
├── Implementation/
│   ├── MotorModule.py            # Motor control module, reused during the real-time implementation phase
│   ├── RunMain.py                # Main script to run the trained model and control the car in real-time
│   ├── WebcamModule.py           # Webcam handling for real-time image capture and model inference
│   └── requirements.txt          # Python package dependencies for real-time implementation
│
└── README.md                     # Documentation of the project

```


## Installation Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/self-driving-vehicle.git
   cd self-driving-vehicle
   ```

2. **Install Python Dependencies**:
   Install essential Python libraries required for the project:
   ```bash
   sudo apt-get update
   sudo apt-get install python3-opencv
   pip install numpy matplotlib tensorflow keras
   ```

3. **Hardware Setup**:
   - Follow the wiring diagram provided in the `docs/hardware_setup.pdf` to connect the motors to the Raspberry Pi using the motor driver.
   - Ensure that the camera is properly connected to the Raspberry Pi.

4. **Configure Motor Control**:  
   Edit the `MotorModule.py` to ensure the GPIO pins used match your hardware configuration.


## 👤 Author 🧑‍💻

**Aditya Sagar**  
[![LinkedIn Logo](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/adityasagarr)  


## Project Pictures  📸
//to be added

---
