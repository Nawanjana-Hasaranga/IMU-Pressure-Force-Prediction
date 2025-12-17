# Sensor Fusion Force Prediction using LSTM

## Project Overview
This project successfully applies Deep Learning (LSTM) to predict vertical ground reaction forces (**Fz**) by fusing data from two distinct sensor types: **IMU** (Accelerometer & Gyroscope) and **Pressure Sensors**. The goal was to overcome the limitations of single-sensor systems to achieve high-accuracy force estimation.

## Key Results
* **Final R² Score: 0.9514** (Improved from a baseline of -0.10)
* **Error Rate:** Extremely low Validation Loss (0.0022 MSE).
* **Performance:** The model accurately captures peak forces up to 1400N and rapid unloading phases with minimal lag.

## Methodology
The solution uses a **Sensor Fusion** approach with a Stacked LSTM architecture:
1. **Data Processing:**
   * Synchronized IMU (acceleration/rotation) and Pressure data.
   * Applied `MinMaxScaler` to normalize all inputs to the [0, 1] range to stabilize gradients.
2. **Model Architecture:**
   * **Input Layer:** Accepts multi-channel sensor data.
   * **LSTM Layers:** Two stacked layers (128 units & 64 units) to learn temporal dependencies.
   * **Dropout:** Applied (0.2) to prevent overfitting.
   * **Output:** Dense layer predicting 3-axis forces (Fx, Fy, Fz).
3. **Training Strategy:**
   * Used **Early Stopping** to automatically detect the optimal training point (Epoch 64) and prevent overfitting.

## Visualization
Below is the comparison between the Actual Target Force (Black) and the LSTM Prediction (Blue). The overlap indicates high precision.

![Fz Prediction Graph](download.png)
*(Note: Ensure the image file name in the repo matches the name in the parentheses above)*

## Tools Used
* Python (Google Colab)
* TensorFlow / Keras
* Pandas & Scikit-Learn
* Matplotlib
