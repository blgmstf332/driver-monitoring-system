# Driver Monitoring System

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square)
![OpenCV](https://img.shields.io/badge/OpenCV-287B50?style=flat-square)
![YOLOv8](https://img.shields.io/badge/YOLOv8-6536BD?style=flat-square)
![MediaPipe](https://img.shields.io/badge/MediaPipe-00897B?style=flat-square)
![Streamlit](https://img.shields.io/badge/Streamlit-C94343?style=flat-square)
![Computer Vision](https://img.shields.io/badge/Computer%20Vision-555555?style=flat-square)

## Project Overview

A real-time computer vision and deep learning prototype for monitoring driver fatigue, drowsiness, distraction, and mobile phone usage. The system integrates facial landmark analysis, CNN-based eye classification, object detection, and real-time alert mechanisms.

## Key Features

- **Drowsiness Detection:** Eye Aspect Ratio (EAR) and eye-state monitoring.
- **Distraction Detection:** Facial landmarks and head orientation analysis.
- **Mobile Phone Detection:** YOLOv8-based object detection.
- **Fatigue Monitoring:** PERCLOS-based eye closure analysis.
- **Yawn Detection:** Mouth Aspect Ratio (MAR) analysis.
- **Automatic Calibration:** Personalized eye closure thresholds.
- **Real-Time Alerts:** Visual and audible warning mechanisms.
- **Session Reporting:** Event logs, optional snapshots, and ZIP export.

## System Architecture

```mermaid
flowchart TD
    A[Webcam Input] --> B[OpenCV Processing]
    B --> C[MediaPipe Facial Landmarks]
    C --> D[EyeCNN Eye Classification]
    B --> E[YOLOv8 Phone Detection]
    C --> F["Behavior Analysis: EAR, MAR, PERCLOS and Rules"]
    D --> F
    E --> F
    F --> G[Dashboard]
    F --> H[Audio Alerts]
    F --> I[Session Reports]
```

## Technical Components

| Component | Implementation |
|---|---|
| Video processing | OpenCV |
| Facial landmarks | MediaPipe Face Landmarker |
| Eye classification | PyTorch CNN |
| Object detection | YOLOv8n |
| Fatigue analysis | EAR and PERCLOS |
| Yawn detection | MAR |
| User interface | Streamlit |
| Audio warnings | Windows winsound |

## CNN Architecture

```mermaid
flowchart TD
    A["Grayscale Eye Image: 64 × 64 (default)"] --> B["Conv2D: 32 Channels"]
    B --> C["Conv2D: 64 Channels"]
    C --> D["Conv2D: 128 Channels"]
    D --> E["Fully Connected: 256 Units"]
    E --> F["Dropout: 0.5"]
    F --> G["Output: Open / Closed"]
```

Convolutional blocks include batch normalization, ReLU activation, and max pooling.

## Repository Structure

```text
driver-monitoring-system/
├── web_app.py
├── surucu_takip.py
├── step1_kamera_test.py
├── eye_model.pt
├── yolov8n.pt
├── face_landmarker.task
├── requirements.txt
└── README.md
```

Session reports and optional snapshots are generated locally during execution.

## Installation & Usage

**Prerequisites:** Python, Windows, and a webcam.

```bash
git clone https://github.com/blgmstf332/driver-monitoring-system.git
cd driver-monitoring-system
pip install -r requirements.txt
```

Streamlit interface:

```bash
streamlit run web_app.py
```

Desktop monitoring:

```bash
python surucu_takip.py
```

Camera test:

```bash
python step1_kamera_test.py
```

## Runtime Monitoring

- Frames per second (FPS)
- Face detection rate
- CNN prediction confidence
- Personalized EAR threshold
- Average PERCLOS
- Detected events and session duration

Runtime statistics and prediction confidence are not substitutes for validated accuracy metrics.

## Limitations & Future Improvements

- Validate performance on an independent, labeled test dataset.
- Include model training scripts and reproducible evaluation.
- Improve detection under varying lighting conditions and camera angles.
- Standardize CNN integration across application versions.
- Add cross-platform camera and audio support.
- Pin dependency versions.
- Improve privacy and secure handling of captured images.

**Disclaimer:** This project is an educational prototype, not a certified automotive safety system. It must not be relied upon to determine whether a person is safe to drive.

## Author

**Mustafa Kılıç**

Computer Engineering Student — Artificial Intelligence, Machine Learning & Data Science

[GitHub](https://github.com/blgmstf332)
