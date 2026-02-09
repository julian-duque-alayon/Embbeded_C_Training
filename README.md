# 🛰️ Embedded C Training

Welcome to my **Embedded C Training** laboratory! This repository is dedicated to my journey in mastering embedded systems, low-level programming, and real-time development.

![C](https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c&logoColor=white)
![STM32](https://img.shields.io/badge/Platform-STM32-03234B?style=for-the-badge&logo=stmicroelectronics&logoColor=white)
![ESP32](https://img.shields.io/badge/Platform-ESP32-E7352C?style=for-the-badge&logo=espressif&logoColor=white)
![Build](https://img.shields.io/badge/Build-CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)

---

## 🎯 Objectives
- [x] Setting up a professional development environment with **CMake** and **Arm GNU Toolchain**.
- [ ] Implement Low-Level (LL) drivers for STM32 peripherals.
- [ ] Master Bare-Metal programming.
- [ ] Explore RTOS (FreeRTOS) and concurrent task management.
- [ ] IoT integration with ESP32.

## 🛠️ Hardware Stack
| Device | Processor | Description |
| :--- | :--- | :--- |
| **NUCLEO-F413ZH** | Cortex-M4 | High-performance STM32 Nucleo-144 board. |
| **ESP32** | Xtensa Dual-Core | Wi-Fi & Bluetooth MCU for IoT projects. |

## 📂 Repository Structure
- `Template/`: A clean, scalable base project for the **NUCLEO-F413ZH**, configured with CMake and LL Drivers.
- *(Coming Soon)* `Lessons/`: Step-by-step guides and specific peripheral exercises.
- *(Coming Soon)* `Projects/`: Full-scale embedded applications.

## 🚀 Getting Started

### Prerequisites
1. **Toolchain**: [gcc-arm-none-eabi](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain)
2. **Build System**: [CMake](https://cmake.org/download/) & Ninja/Make.
3. **Debugger**: OpenOCD or ST-Link Utility.

### Building the Template
```bash
cd Template
mkdir build && cd build
cmake .. -G Ninja
ninja
```

---
Developed with ❤️ by [Julian Duque](https://github.com/julian-duque-alayon)
