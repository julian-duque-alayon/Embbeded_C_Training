# 🛰️ Embedded C Training

Embedded systems training laboratory for **STM32** and **ESP32** microcontrollers.

---

## 📂 Repository Structure

### [STM32](./STM32)
Projects for the STM32 family, specifically focused on the **NUCLEO-F413ZH** board.
- **[Template_NucleoF413ZH](./STM32/Template_NucleoF413ZH)**: Base project with CMake and Low-Layer (LL) Drivers.

### [ESP32](./ESP32)
Projects for **ESP32** (Wi-Fi/Bluetooth IoT systems).
- **[Template](./ESP32/Template)**: Base structure for ESP-IDF / Arduino projects.

---

## 🛠️ VS Code Workflow (Multi-Project Setup)

Since this repository contains multiple independent CMake projects, follow these steps to ensure the IDE (VS Code with CMake Tools) works correctly:

### 1. Select the Active Project
If you have the whole repository open, you must tell VS Code which sub-folder is the active project:
- Press `Ctrl + Shift + P`
- Search for: **`CMake: Select Active Folder`**
- Choose the specific template you want to work on (e.g., `Template_NucleoF413ZH`).

### 2. Configure the Kit (Toolchain)
You need to tell the IDE which compiler to use:
- Press `Ctrl + Shift + P`
- Command: **`CMake: Select a Kit`**
- **For STM32**: Select `arm-none-eabi`.
- **For ESP32**: Select the corresponding ESP-IDF toolchain.

### 3. Build & Compile
- **Select Build Target**: `Ctrl + Shift + P` -> **`CMake: Select Variant`** (usually `Debug` or `Release`).
- **Build**: Press `F7` or click the **Build** button in the status bar.
- **Clean Configuration (Cache)**: If you experience weird errors after changing paths or files, run:
  - `Ctrl + Shift + P` -> **`CMake: Delete Cache and Reconfigure`**.

---
*Developed by [Julian Duque](https://github.com/julian-duque-alayon)*
