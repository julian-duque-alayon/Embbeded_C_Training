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

## 🛠️ Development Workflow (Multi-Project)

Since this repository contains multiple independent projects (STM32 weeks, templates, etc.), you must explicitly tell VS Code which one you are currently working on.

### 1. Selecting your Active Project (The IDE Way)
If you have the entire repository open, you need to set the "Context" for the CMake tools:
1.  **Select Active Folder**: Press `Ctrl + Shift + P` and search for **`CMake: Select Active Folder`**. Choose the directory you want to build (e.g., `STM32/Week_1`).
2.  **Select a Kit**: Press `Ctrl + Shift + P` -> **`CMake: Select a Kit`**.
    *   **For STM32**: Choose `arm-none-eabi`.
    *   **For ESP32**: Choose the ESP-IDF toolchain.
3.  **Configure**: The IDE will automatically look for the `CMakeLists.txt` inside that folder.

### 2. Using the VS Code Buttons (The "Play" Button)
The status bar at the bottom provides quick actions configured via the `.vscode/` files:
*   **⚙️ Build**: Compiles your code.
*   **▶️ Run/Debug**: The "Play" button (or `F5`) is configured in `.vscode/launch.json`. It will use **Cortex-Debug** and **OpenOCD** to flash the code and start a debugging session.
*   **⚡ Flash (Task)**: To just flash without debugging, press `Ctrl + Shift + B` and select **"Flash Nucleo"**. This uses the task defined in `.vscode/tasks.json`.

---

### 3. The "Pro" Way (Manual Terminal Commands)
If you prefer the terminal or are troubleshooting, use these commands from the root of your sub-project (e.g., inside `STM32/Week_1/`):

#### **A. Build & Compile**
```bash
# 1. Create the build directory and configure
cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake

# 2. Compile the project
cmake --build build
```

#### **B. Flash the Board**
```bash
# Uses OpenOCD to send the .elf to the chip
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program build/Nucleo_F413_Template.elf verify reset exit"
```

#### **C. Manual Debugging**
If not using the IDE button, you can start an OpenOCD server in one terminal:
```bash
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg
```
Then, in another terminal, connect using `gdb-multiarch`:
```bash
arm-none-eabi-gdb build/Nucleo_F413_Template.elf -ex "target remote localhost:3333"
```

---
*Developed by [Julian Duque](https://github.com/julian-duque-alayon)*
