# 🏗️ Nucleo-F413ZH Project Template

This template provides a professional, lightweight starting point for developing on the **STM32F413ZH** microcontroller using **Low-Layer (LL) Drivers** and **CMake**.

## 🚀 Quick Start (WSL/Linux Terminal)

### 1. Build the Project
Run the following commands within this directory:

```bash
# Configure the build system
cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake

# Compile and generate binaries
cmake --build build
```

### 2. Flash the Microcontroller
Ensure the hardware is attached to WSL via `usbipd` (see [STM32/README.md](../README.md)), then run:

```bash
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program build/Nucleo_F413_Template.elf verify reset exit"
```

## 📂 Project Highlights

- **Drivers**: Utilizes exclusively **STM32 Low-Layer (LL)** drivers for minimal overhead and direct hardware control.
- **Boot**: Includes official CMSIS startup code and vector table in the `Startup/` folder.
- **Linker**: Pre-configured `STM32F413XX_FLASH.ld` for 1.5MB Flash and 320KB RAM.
- **Automation**: The build process automatically generates a `.hex` file and prints the output memory size.

## 🔧 Project Structure

- `App/`: Contains your application logic (`main.c`, interrupts).
- `Drivers/`: Peripheral drivers (CMSIS & STM32 LL).
- `Startup/`: Device-specific assembly startup code.
- `cmake/`: Toolchain configuration for cross-compiling.
- `CMakeLists.txt`: Main build logic.

---
*Back to [STM32 Modules](../README.md)*
