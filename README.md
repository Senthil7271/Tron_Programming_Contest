# TRON – Offline Embedded OCR & Voice Assistant.

## Overview

**TRON** is a fully offline embedded AI assistant designed for the **Renesas EK-RA8P1** development board. The system combines OCR, speech interaction, environmental sensing, and a graphical user interface into a single portable platform.

Unlike cloud-based assistants, TRON performs all processing locally without requiring an internet connection, making it suitable for industrial, educational, and privacy-sensitive applications.

---

# Features

- Offline OCR (Optical Character Recognition)
- Offline Speech-to-Text (Voice Commands)
- Offline Text-to-Speech
- Chatbot Interface
- Environmental Monitoring
- LCD Touchscreen GUI
- Camera Image Capture
- Microphone Input
- Speaker Output
- SD Card Storage
- Real-Time Operating System (µT-Kernel 3.0)

---

# Hardware

## Main Controller

- Renesas EK-RA8P1
- ARM Cortex-M85
- ARM Cortex-M33
- Arm Ethos-U55 NPU

---

## Display

- MIPI LCD Touch Display

---

## Camera

- MIPI CSI Camera Module

---

## Audio

### Microphone

- Digital I2S MEMS Microphone

### Speaker

- MAX98357A I2S Audio Amplifier
- 8Ω Speaker

---

## Environmental Sensors

### SCD40

Measures

- CO₂ Concentration
- Temperature
- Humidity

Communication

- I²C

---

## Storage

- Micro SD Card

Used for

- OCR Models
- Fonts
- Dictionary
- Images
- Audio Files
- Configuration Files

---

# Software Stack

```
Application
      │
      ▼
GUI
      │
      ▼
Offline Chatbot
      │
      ├────────────┐
      ▼            ▼
 OCR Engine    Voice Interface
      │            │
      ▼            ▼
Camera      STT / TTS
      │            │
      └──────┬─────┘
             ▼
      µT-Kernel 3.0
             │
             ▼
      Renesas FSP
             │
             ▼
      RA8P1 Hardware
```

---

# Project Architecture

```
                Camera
                   │
                   ▼
            OCR Engine
                   │
                   ▼
             Extracted Text
                   │
                   ▼
          Offline Chatbot
            ▲         │
            │         ▼
      Speech-to-Text  Response
            ▲         │
            │         ▼
       Microphone  Text-to-Speech
                      │
                      ▼
                   Speaker


SCD40
CO₂
Temperature
Humidity
      │
      ▼
 LCD Dashboard
```

---

# Directory Structure

```
TRON/
│
├── docs/
│
├── firmware/
│   ├── src/
│   ├── inc/
│   ├── drivers/
│   ├── middleware/
│   └── rtos/
│
├── models/
│   ├── ocr/
│   ├── chatbot/
│   └── speech/
│
├── assets/
│   ├── fonts/
│   ├── images/
│   └── icons/
│
├── sdcard/
│
├── tools/
│
├── hardware/
│
└── README.md
```

---

# Functional Modules

## 1. OCR Module

- Capture image
- Image preprocessing
- Text detection
- Text recognition
- Display extracted text

---

## 2. Voice Module

- Wake word (optional)
- Speech capture
- Speech-to-Text
- Command processing
- Text-to-Speech

---

## 3. Chatbot Module

- Offline inference
- Context handling
- Response generation
- Voice output
- Display output

---

## 4. Environmental Monitoring

Displays

- CO₂
- Temperature
- Humidity

Updates continuously on LCD.

---

## 5. GUI

Features

- Touch Interface
- OCR Screen
- Chat Screen
- Sensor Dashboard
- Settings
- Image Viewer

---

# System Workflow

```
Power ON
     │
     ▼
Initialize Hardware
     │
     ▼
Initialize µT-Kernel
     │
     ▼
Initialize LCD
     │
     ▼
Initialize Camera
     │
     ▼
Initialize Microphone
     │
     ▼
Initialize Speaker
     │
     ▼
Initialize SCD40
     │
     ▼
Load Models
     │
     ▼
Main Menu
     │
     ├──────── OCR
     │
     ├──────── Voice Assistant
     │
     ├──────── Chatbot
     │
     └──────── Sensor Dashboard
```

---

# Development Environment

- e² studio
- Renesas Flexible Software Package (FSP)
- GCC ARM Toolchain
- µT-Kernel 3.0
- Git
- Python (Model Conversion Utilities)

---

# Hardware Connections

| Module | Interface |
|---------|-----------|
| LCD | MIPI DSI |
| Camera | MIPI CSI |
| Microphone | I2S |
| MAX98357A | I2S |
| SCD40 | I²C |
| SD Card | SDHI |
| Touch | I²C |

---

# Future Improvements

- Face Recognition
- QR Code Scanner
- Barcode Scanner
- Document Scanner
- Multi-language OCR
- AI Translation
- Voice Authentication
- Object Detection
- Gesture Recognition
- Wi-Fi Synchronization
- Bluetooth Connectivity
- Cloud Backup (Optional)

---

# Applications

- Smart Education
- Assistive Technology
- Industrial Inspection
- Portable Document Reader
- Smart Home Assistant
- Warehouse Automation
- Healthcare Devices
- Embedded AI Research
- Edge Computing
- IoT Monitoring

---

# Project Status

| Module | Status |
|---------|--------|
| µT-Kernel 3.0 Port | ✅ Completed |
| LCD Driver | ✅ Completed |
| Camera Interface | 🔄 In Progress |
| OCR Integration | 🔄 In Progress |
| Speech-to-Text | ⏳ Planned |
| Text-to-Speech | ⏳ Planned |
| Chatbot | ⏳ Planned |
| SCD40 Sensor | ✅ Working |
| GUI | 🔄 In Progress |
| SD Card Support | ⏳ Planned |

---

# Authors

**Senthil Kumar Mahalingam**

Department of Electronics Engineering (VLSI)

Chennai Institute of Technology

---

# License

This project is intended for educational, research, and embedded AI development purposes.
