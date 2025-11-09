# 🌱 TechnoGrow: Solar-Powered Hydroponic Farming System

[![IEEE Lumina 2025](https://img.shields.io/badge/IEEE-Lumina%202025-blue)](https://github.com/CICR-The-Robotics-Hub-of-JIIT-128/TechnoGrow-Solar-Powered-Hydroponic-Farming-System)
[![Python](https://img.shields.io/badge/Python-3.x-brightgreen.svg)](https://www.python.org/)
[![Arduino](https://img.shields.io/badge/Arduino-Compatible-00979D.svg)](https://www.arduino.cc/)

> **An innovative solution that promotes sustainable and automated agriculture through solar-powered hydroponic farming with real-time environmental monitoring.**

TechnoGrow harnesses solar energy to power hydroponic water circulation and environmental monitoring, ensuring optimal growth conditions for plants without the use of soil. This project was showcased at the **IEEE Lumina Project Exhibition**.

![Dashboard Preview](https://img.shields.io/badge/Status-Active-success)

---

## 📋 Table of Contents

- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Software Requirements](#-software-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Dashboard Overview](#-dashboard-overview)
- [How It Works](#-how-it-works)
- [Team](#-team)

---

## ✨ Features

### 🔹 Real-Time Environmental Monitoring
- **Temperature Monitoring**: Continuous tracking using DHT11 sensor
- **Humidity Monitoring**: Real-time humidity levels for optimal plant growth
- **Gas Level Detection**: MQ4 sensor for detecting methane and other gases

### 🔹 Automated Alert System
- Visual alerts based on gas concentration levels:
  - ✅ **Safe** (< 50%): Green indicator
  - 🟡 **Moderate** (50-80%): Yellow warning
  - ⚠️ **High** (> 80%): Red alert for immediate action

### 🔹 Smart Dashboard
- Live data visualization with animated graphs
- Real-time updates every 3 seconds
- Rolling 50-point data window for performance optimization
- Color-coded environment status
- Historical trend analysis

### 🔹 Sustainable Energy
- Solar-powered system for hydroponic water circulation
- Renewable energy integration with IoT technology
- Eco-friendly and cost-effective solution

---

## 🏗️ System Architecture

```
┌─────────────────────┐
│   Solar Panel       │
│   (Power Source)    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   Arduino Board     │
│   (Controller)      │
├─────────────────────┤
│  - DHT11 Sensor     │ ──► Temperature & Humidity
│  - MQ4 Sensor       │ ──► Gas Detection (CH₄)
│  - Water Pump       │ ──► Hydroponic Circulation
└──────────┬──────────┘
           │
           ▼ (Serial USB)
┌─────────────────────┐
│   Python Dashboard  │
│   (Visualization)   │
├─────────────────────┤
│  - pandas           │
│  - matplotlib       │
│  - pyserial         │
└─────────────────────┘
```

---

## 💻 Software Requirements

### Python Dependencies
```bash
Python 3.x
pandas
matplotlib
pyserial
```

### Arduino IDE
- Arduino IDE (latest version)
- DHT sensor library
- MQ4 sensor library

---

## 📦 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/CICR-The-Robotics-Hub-of-JIIT-128/TechnoGrow-Solar-Powered-Hydroponic-Farming-System.git
cd TechnoGrow-Solar-Powered-Hydroponic-Farming-System
```

### 2. Install Python Dependencies

```bash
pip install pandas matplotlib pyserial
```

### 3. Arduino Setup

1. Open Arduino IDE
2. Install required libraries:
   - DHT sensor library (by Adafruit)
   - MQ4 sensor library
3. Upload the Arduino sketch to your board
4. Note the COM port (e.g., COM5 on Windows, /dev/ttyUSB0 on Linux)

### 4. Configure Serial Port

Edit `serial.py` and update the COM port:

```python
ser = serial.Serial('COM5', 9600)  # Change COM5 to your port
```

---

## 🚀 Usage

### Running the Dashboard

1. **Connect Arduino** to your computer via USB
2. **Ensure sensors are connected** and Arduino is powered on
3. **Run the Python dashboard**:

```bash
python serial.py
```

### Expected Behavior

- A real-time dashboard window will open
- Data will update every 3 seconds
- The dashboard displays:
  - 🌡️ **Temperature** in °C (Red line)
  - 💧 **Humidity** in % (Blue line)
  - 🧪 **Gas Level** in % (Green line)
  - Status indicator (Safe/Moderate/High)

---

## 📊 Dashboard Overview

- **Real-Time Graphs** with temperature, humidity, and gas levels
- **Live Readings** for each parameter
- **Status Indicator** for air safety
- **Dynamic Background Colors** for quick understanding

---

## ⚙️ How It Works

### Data Flow

1. **Sensor Reading**
   - Arduino reads DHT11 (temperature & humidity)
   - Arduino reads MQ4 (gas concentration)
   - Data formatted as: `DATA,temperature,humidity,gas`

2. **Serial Communication**
   - Arduino sends data via USB serial (9600 baud)
   - Python reads and parses incoming data

3. **Data Processing**
   - Stored in pandas DataFrame with timestamps
   - Rolling window of last 50 readings

4. **Visualization**
   - matplotlib animates the graph in real-time
   - Color-coded status indicator

### Arduino Data Format

```
DATA,25.5,60.2,35.8
```

Where:
- `DATA` = Identifier
- `25.5` = Temperature (°C)
- `60.2` = Humidity (%)
- `35.8` = Gas level (%)

---

## 👨‍💻 Team

- **Harshit Pandey** 
- **Tulika Aggarwal** 
- **Krishna Pandey** 
- **Amritesh Singh** 

---

<div align="center">

### 💡 Building the Future of Smart Farming 🌱

**Made with ❤️ by the TechnoGrow Team**

</div>
