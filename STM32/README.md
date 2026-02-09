# 🏗️ STM32F413ZH Project Template

This is a professional base template configured with **CMake** and **Low-Layer (LL) Drivers** specifically for the **NUCLEO-F413ZH** (Cortex-M4) development board.

---

## 🚀 Workflow (WSL + Hardware)

Since the hardware is physically connected to Windows but we compile in WSL, follow these steps:

### 1. Windows Preparation (PowerShell)
You must "pass" the USB port from Windows to WSL using `usbipd`.

1.  **List Devices**: Find the BUSID of your STM32 (look for ST-LINK).
    ```powershell
    usbipd list
    ```
2.  **Attach to WSL**: (Replace `2-8` with your actual BUSID).
    ```powershell
    usbipd attach --wsl --busid 2-8 --auto-attach
    ```

### 2. WSL Verification
Confirm that WSL can see the device.

1.  **List USBs**: You should see an entry for "STMicroelectronics ST-LINK".
    ```bash
    lsusb
    ```

### 3. Build & Compilation (WSL Terminal)
Inside this directory (`STM32/Template_NucleoF413ZH`):

1.  **Configure Project**:
    ```bash
    cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake
    ```
2.  **Compile**:
    ```bash
    cmake --build build
    ```

### 4. Flash the Microcontroller
Upload the code from WSL using **OpenOCD**.

1.  **Flash Command**:
    ```bash
    openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program build/Nucleo_F413_Template.elf verify reset exit"
    ```

---

## 📂 Technical Details
- **MCU**: STM32F413ZHT6
- **Drivers**: STM32 Low-Layer (LL) for maximum efficiency.
- **Linker Script**: `STM32F413XX_FLASH.ld` configured for 1.5MB Flash and 320KB SRAM.

---
*Part of [Embedded C Training](https://github.com/julian-duque-alayon/Embbeded_C_Training)*
