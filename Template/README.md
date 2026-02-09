# 🏗️ STM32F413ZH Project Template

A professional-grade **CMake-based** template for the **NUCLEO-F413ZH** development board. This template is designed for developers who prefer a clean, manual workflow over heavy IDEs, utilizing the **STM32 Low-Layer (LL) Drivers** for high efficiency.

## ✨ Features
- **Modern Build System**: Full CMake support with toolchain integration.
- **Lightweight**: Pre-configured to use **Low-Layer (LL) Drivers** (smaller footprint than HAL).
- **Post-Build Automation**: Automatically generates `.hex` files and calculates memory usage (text, data, bss).
- **Standard Layout**: Organized directory structure suitable for professional projects.

## 📁 Directory Structure
```text
Template/
├── App/                # Application logic (main.c, interrupts)
│   ├── inc/            # Header files
│   └── src/            # Source files
├── Drivers/            # CMSIS and STM32 Peripheral Drivers
├── Startup/            # Boot code and Vector Table (.s)
├── cmake/              # Toolchain definitions
├── CMakeLists.txt      # Main build configuration
└── STM32F413XX_FLASH.ld # Linker script for Flash/RAM mapping
```

## 🛠️ Build Instructions

1. **Configure the project**:
   Use the provided toolchain file to set up the build environment.
   ```bash
   cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake
   ```

2. **Compile**:
   ```bash
   cmake --build build
   ```

3. **Output Artifacts**:
   - `Nucleo_F413_Template.elf`: Binary for debugging.
   - `Nucleo_F413_Template.hex`: Flashable image.
   - `Nucleo_F413_Template.map`: Memory map analysis.

## 🔧 Customization
- **Compiler Flags**: Modify `cmake/stm32_gcc.cmake` to adjust optimization levels (`-O2`, `-Os`) or CPU features.
- **Linker Script**: All memory regions are defined in `STM32F413XX_FLASH.ld`. Modify this if you use custom bootloaders or specific RAM sections.
- **Peripherals**: Add or remove LL driver source files in the `file(GLOB_RECURSE ...)` section of the main `CMakeLists.txt`.

---
*Part of the [Embedded C Training](https://github.com/julian-duque-alayon/Embbeded_C_Training) series.*
