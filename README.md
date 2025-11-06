# Plant Diseases Detection  
> A project to detect plant diseases using embedded systems (ESP32 + Raspberry Pi) and AI (ResNet-50).  

## Table of Contents  
- [Overview](#overview)  
- [Features](#features)  
- [Architecture](#architecture)  
- [Getting Started](#getting-started)  
  - [Prerequisites](#prerequisites)  
  - [Installation](#installation)  
  - [Running the System](#running-the-system)  
- [Usage](#usage)  
- [Project Structure](#project-structure)  
- [Dataset & Model](#dataset--model)  
- [Hardware Setup](#hardware-setup)  
- [Results & Metrics](#results--metrics)  
- [Contributing](#contributing)  
- [License](#license)  
- [Acknowledgements](#acknowledgements)  

---

## Overview  
This project aims to detect diseases in plants by integrating embedded systems and deep learning. A sensor module (ESP32) reads environmental data (temperature, humidity, light) and sends it to a Raspberry Pi, which captures a photo of the plant’s leaf, runs a pre-trained deep-learning model to classify disease, and displays the result. The model used is based on ResNet‑50 and the dataset used is PlantVillage.  

It is aligned with the goal of building socially and environmentally impactful applications (detecting plant disease early to reduce crop loss).

---

## Features  
- Embedded sensor readings: temperature (BMP280), humidity, light intensity.  
- Camera capture on Raspberry Pi when triggered.  
- Deep-learning inference (ResNet-50) to label plant disease.  
- Display of sensor readings and prediction result on screen (or via console).  
- Modular architecture: separation between embedded device (ESP32) and host (Raspberry Pi).  

---

## Architecture  
1. **ESP32** module: reads sensors (BMP280, humidity, luminosity), sends UART data to Raspberry Pi.  
2. **Raspberry Pi**: listens on UART, when button pressed:  
   - reads latest sensor values  
   - captures image via USB camera  
   - runs inference with model to detect disease  
   - displays result on screen or logs it.  
3. **Model & Dataset**: Fine-tuned ResNet-50 on the PlantVillage dataset, without (initially) data augmentation.  

---

## Getting Started  

### Prerequisites  
- Raspberry Pi 4 (or similar) running Linux (e.g., Raspbian/Ubuntu).  
- ESP32 board + sensors (BMP280, humidity sensor, light sensor) + USB camera + button.  
- Python 3.x environment (on Raspberry Pi).  
- Required libraries: `torch`, `torchvision`, `opencv-python`, `pyserial`, etc.  
- Dataset: PlantVillage (accessible externally).  

### Installation  
Clone the repository:
```bash
git clone https://github.com/AymenENSI/Plant-Diseases-Detection.git
cd Plant-Diseases-Detection
