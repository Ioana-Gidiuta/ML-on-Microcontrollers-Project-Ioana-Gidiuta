# 👋 Hand Gesture Recognition on Microcontrollers Using Radar

**Author:** Ioana Gidiuta  
**Course:** 227-0155-00L Machine Learning on Microcontrollers FS2025  
**Group:** 01  
**Institution:** ETH Zurich  

---

## Overview

This project focuses on **hand gesture recognition** using radar signals captured by **Acconeer XR112 sensors**, optimized for **deployment on resource-constrained microcontrollers**.

The project is based on the **TinyRadarNN 11G Dataset** [Scherer et al., TinyRadarNN, IEEE J. IoT, 2021 https://doi.org/10.1109/JIOT.2021.3067382], which includes:
- **11 main hand gestures**
- **2 additional gestures**: *No Hand*, *Random Gesture*
- **160 Hz sweep frequency**
- **2 radar sensors (antennas)**
- **46 recordings per gesture (~3 seconds each)**

A total of **23 models** were developed, trained, and evaluated with different configurations, focusing on trade-offs between **accuracy, latency, and memory**.

## 📌 Project Goals & Contributions

-  Integrated **Radar-based features**: RTM, DTM, ATM, Energy, Signal Variation (SOR, SOT, 2D)
-  Performed **model compression**: Quantization (int8), Knowledge Distillation, Model Pruning
- Built and trained **23 models**, evaluated extensively on validation data
-  Focused on optimizing:
    - **Flash size (KB)**
    - **RAM usage**
    - **Inference latency**
- Deployed **5 selected models** on:
  - **ST B-U585I-IOT02A**
  - **ST B-L475E-IOT01A2**
-  Created live and recorded inference demos
- Visualized trade-offs:
  - Accuracy vs Flash
  - RAM vs Accuracy
  - Latency vs Energy

---

## 📊 Evaluation Highlights

| Metric               | Range / Achievements                    |
|----------------------|------------------------------------------|
| Accuracy             | Up to **98.4%** (float32)               |
| Best int8 Accuracy   | **87.31%** (6CNN-1DC)         |
| Smallest Model       | ~**29KB**, >80% accuracy (3CNN-LSTM int8) |
| Fastest Model        | <**550 ms/sample**                      |
| MACC Range           | 15M to 80M                              |
| Platforms            | STM32-based microcontrollers            |

---

## 🔧 Deployment Targets

### B-U585I-IOT02A
- **RAM**: 786 KB  
- **Flash**: 2 MB  
- **Features**: Cortex-M33, Wi-Fi, BLE, sensors

### B-L475E-IOT01A2
- **RAM**: 320 KB  
- **Flash**: 1 MB  
- **Features**: Cortex-M4, BLE, sensors, LoRa, Wi-Fi

---

## Model Highlights

| Model Name                   | Size (KB) | Accuracy (%) |
|------------------------------|-----------|--------------|
| 2CNN-1DC + Distill (int8     | 46.8      | 78.74        |
| 3CNN-1DC + Distill (int8)    | 51.2      | 80.1         |
| 6CNN-1DC          (int8)     | 63.7      | 87.31        |
| 3CNN-LSTM + Distill (int8)   | 29        | 83           |
| 6CNN-LSTM         (int8)     | 40        | 85.76        |

> Full comparison and graphs available in `Graph_Generation_Comparison.ipynb`.
