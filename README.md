# 🌱 TechnoGrow: Solar-Powered Hydroponic Farming System

[![IEEE Lumina 2025](https://img.shields.io/badge/IEEE-Lumina%202025-blue)](https://github.com/CICR-The-Robotics-Hub-of-JIIT-128/TechnoGrow-Solar-Powered-Hydroponic-Farming-System)
[![Python](https://img.shields.io/badge/Python-3.x-brightgreen.svg)](https://www.python.org/)
[![Arduino](https://img.shields.io/badge/Arduino-Compatible-00979D.svg)](https://www.arduino.cc/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **An innovative solution that promotes sustainable and automated agriculture through solar-powered hydroponic farming with real-time environmental monitoring.**

TechnoGrow harnesses solar energy to power hydroponic water circulation and environmental monitoring, ensuring optimal growth conditions for plants without the use of soil. This project was showcased at the **IEEE Lumina Project Exhibition** by students from CICR (Creativity and Innovation Cell in Robotics).

![Dashboard Preview](https://img.shields.io/badge/Status-Active-success)

---

## 📋 Table of Contents

- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Hardware Requirements](#-hardware-requirements)
- [Software Requirements](#-software-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Dashboard Overview](#-dashboard-overview)
- [How It Works](#-how-it-works)
- [Team](#-team)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

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

## 🔧 Hardware Requirements

| Component | Description | Quantity |
|-----------|-------------|----------|
| **Arduino Board** | Uno/Nano/Mega (any compatible) | 1 |
| **DHT11 Sensor** | Temperature & Humidity sensor | 1 |
| **MQ4 Gas Sensor** | Methane & gas detection | 1 |
| **Solar Panel** | 12V solar panel for power | 1 |
| **Water Pump** | 12V DC submersible pump | 1 |
| **Relay Module** | For pump control | 1 |
| **Battery Pack** | Backup power storage | 1 |
| **Hydroponic Setup** | PVC pipes/containers | As needed |
| **Jumper Wires** | For connections | Multiple |
| **Breadboard** | For prototyping | 1 |

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

**Finding your port:**
- **Windows**: Device Manager → Ports (COM & LPT)
- **Linux**: Run `ls /dev/tty*` or `dmesg | grep tty`
- **Mac**: Run `ls /dev/tty.*`

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

### Stopping the Dashboard

- Close the matplotlib window, or
- Press `Ctrl+C` in the terminal

---

## 📊 Dashboard Overview

### Main Features

1. **Real-Time Graph**
   - Three-line plot showing all sensor readings
   - X-axis: Time stamps (HH:MM:SS)
   - Y-axis: Sensor values
   - Rolling window of last 50 data points

2. **Live Readings Display**
   - Bottom-left corner shows current values
   - Updates with each data refresh

3. **Status Indicator**
   - Top-right corner shows environment status
   - Color-coded for quick visual assessment
   - Automatic background color change based on gas levels

4. **Dynamic Background**
   - 🟢 **Green**: Safe environment (Gas < 50%)
   - 🟡 **Yellow**: Moderate warning (Gas 50-80%)
   - 🔴 **Red**: High alert (Gas > 80%)

---

## ⚙️ How It Works

### Data Flow

1. **Sensor Reading**
   - Arduino reads DHT11 (temperature & humidity)
   - Arduino reads MQ4 (gas concentration)
   - Data is formatted as: `DATA,temperature,humidity,gas`

2. **Serial Communication**
   - Arduino sends data via USB serial (9600 baud)
   - Python script reads and parses the data

3. **Data Processing**
   - Parsed data is stored in pandas DataFrame
   - Last 50 readings are maintained (memory optimization)
   - Timestamp is added to each reading

4. **Visualization**
   - matplotlib animates the graph every 3 seconds
   - Status is calculated based on gas levels
   - UI updates with latest values and trends

### Arduino Data Format

```
DATA,25.5,60.2,35.8
```
Where:
- `DATA` = Message identifier
- `25.5` = Temperature in °C
- `60.2` = Humidity in %
- `35.8` = Gas level in %

---

## 👨‍💻 Team

This project was developed by students from **CICR (Creativity and Innovation Cell in Robotics)**:

- **Harshit Pandey** (Team Lead) - 1st Year Diploma
- **Tulika Aggarwal** - Developer
- **Krishna Pandey** - Developer
- **Amritesh Singh** - Developer

### About CICR

CICR is the Robotics Hub of JIIT-128, dedicated to fostering innovation and creativity in robotics and IoT. We believe in leveraging technology for sustainability and smart solutions.

---

## 🤝 Contributing

We welcome contributions to improve TechnoGrow! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Areas for Improvement

- [ ] Add data logging to CSV/database
- [ ] Implement email/SMS alerts for critical conditions
- [ ] Add web-based dashboard (Flask/Django)
- [ ] Include more sensors (pH, EC, light intensity)
- [ ] Develop mobile app integration
- [ ] Add machine learning for predictive analysis
- [ ] Create Arduino firmware code repository

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **IEEE Lumina 2025** - For providing the platform to showcase our innovation
- **JIIT-128** - For institutional support
- **CICR** - For resources and mentorship
- **Open Source Community** - For amazing tools and libraries

---

## 📞 Contact & Support

- **GitHub**: [CICR-The-Robotics-Hub-of-JIIT-128](https://github.com/CICR-The-Robotics-Hub-of-JIIT-128)
- **Project Issues**: [Report a Bug](https://github.com/CICR-The-Robotics-Hub-of-JIIT-128/TechnoGrow-Solar-Powered-Hydroponic-Farming-System/issues)

---

## 🌟 Star Us!

If you find this project useful, please consider giving it a ⭐ on GitHub!

---

<div align="center">

### 💡 Building the Future of Smart Farming 🌱

**Made with ❤️ by CICR Team**

[![CICR](https://img.shields.io/badge/CICR-Robotics%20Hub-orange)](https://github.com/CICR-The-Robotics-Hub-of-JIIT-128)
[![IEEE](https://img.shields.io/badge/IEEE-Lumina%202025-blue)](https://ieee.org)

</div>