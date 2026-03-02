# TeleICU - Real-Time Computer Vision Patient Monitoring System

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python) ![YOLOv8](https://img.shields.io/badge/YOLOv8-Object%20Detection-green?style=flat-square) ![OpenCV](https://img.shields.io/badge/OpenCV-4.x-red?style=flat-square&logo=opencv) ![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-orange?style=flat-square&logo=pytorch)

An end-to-end computer vision system for real-time ICU patient monitoring.

---

## Problem

ICU patients require continuous monitoring, but round-the-clock human supervision is resource-intensive and prone to fatigue-related delays. In understaffed or remote hospitals, this creates critical gaps in patient care.

## Solution

This system automates ICU surveillance using video analytics - detecting who is present, identifying abnormal motion, and classifying patient activity including seizures in real time. Three independent models were built and benchmarked.

---

## Three Models - One Pipeline

### Model 1 - YOLOv8 Person Detection and Classification
- Fine-tuned YOLOv8 on a custom TeleICU dataset sourced via Roboflow
- Classifies individuals as: Patient, Nurse, Doctor, Background
- Handles occlusion, varied lighting, and class imbalance in clinical environments
- Evaluated using confusion matrices and precision-confidence curves

### Model 2 - Frame Differencing (Motion Detection)
- Built using OpenCV frame-differencing pipeline
- Compares consecutive frames to detect and highlight motion regions
- Draws bounding boxes around detected movement areas in real time

### Model 3 - Background Subtraction and Activity Classification
- Uses MOG2 background subtraction with contour detection
- Classifies detected motion as: Walking, Standing, or Seizure
- Classification based on bounding box geometry (aspect ratio, area, movement pattern)
- Robust to gradual lighting changes typical in ICU environments

---

## Results

All three models were evaluated on identical ICU video inputs for fair comparison.

**Confusion Matrix**

![Confusion Matrix](M1-Confusion%20Matrix.jpg)

**Precision vs Confidence Curve**

![Precision Curve](M1-Precision_Curve.jpg)

**Sample Predictions**

![Prediction 1](M1-Predicte%20OP1.jpg) ![Prediction 2](M1-Predicted%20OP2.jpg)

**Video Outputs**
- MODEL-2-VIDEO-OUTPUT.mp4 - Frame differencing motion detection output
- MODEL-3-VIDEO-OUTPUT.mp4 - Background subtraction activity classification output

---

## Tech Stack

| Component | Technology |
|---|---|
| Object Detection | YOLOv8 (Ultralytics) |
| Motion Detection | OpenCV frame differencing |
| Activity Classification | OpenCV MOG2, Contour Analysis |
| Deep Learning | PyTorch |
| Data Processing | NumPy, Pandas |
| Dataset | Roboflow custom TeleICU |
| Environment | Jupyter Notebook, Python 3.8+ |

---

## Getting Started



---

## Key Challenges Solved

- **Class imbalance** - Far more background frames than activity frames; addressed through dataset balancing and augmentation
- **Occlusion** - Patients partially hidden by equipment; domain-specific YOLOv8 fine-tuning improved robustness
- **Low-light conditions** - Variable ICU lighting; MOG2 adaptive background modelling handles this effectively
- **Real-time performance** - All models designed for frame-by-frame processing on standard hardware

---

## Author

**Vatsala Misra** - B.Tech ECE, VIT Bhopal (2025)

vatsm2003@gmail.com | linkedin.com/in/vatsala-misra | github.com/VatsalaMisra

---

## Acknowledgement

Developed under the Intel Unnati Industrial Training 2024 program at VIT Bhopal University.
Mentor: Dr. Soumitra Keshari Nayak
