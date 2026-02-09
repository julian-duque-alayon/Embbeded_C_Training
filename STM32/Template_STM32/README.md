# 🏗️ STM32F413ZH Project Template

Este es un template base profesional configurado con **CMake** y **Low-Layer (LL) Drivers** específicamente para la placa de desarrollo **NUCLEO-F413ZH** (Cortex-M4).

---

## 🚀 Flujo de Trabajo (WSL + Hardware)

Como el hardware está conectado físicamente a Windows pero compilamos en WSL, sigue estos pasos:

### 1. Preparación en Windows (PowerShell)
Primero, debemos "pasar" el puerto USB del microcontrolador de Windows a WSL.

1.  **Listar dispositivos**: Para ver el BUSID de tu STM32.
    ```powershell
    usbipd list
    ```
2.  **Vincular y Compartir**: (Sustituye `2-8` por el BUSID que viste arriba).
    ```powershell
    usbipd attach --wsl --busid 2-8 --auto-attach
    ```

### 2. Verificación en WSL
Una vez vinculado, confirma que WSL ve el dispositivo.

1.  **Listar USBs**: Deberías ver una entrada que mencione "STMicroelectronics ST-LINK".
    ```bash
    lsusb
    ```

### 3. Construcción y Compilación (WSL)
Dentro de este directorio (`STM32/Template_STM32`):

1.  **Configurar el proyecto**:
    ```bash
    cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake
    ```
2.  **Compilar**:
    ```bash
    cmake --build build
    ```

### 4. Cargar el programa (Flash)
Para subir el código al microcontrolador desde WSL usamos **OpenOCD**.

1.  **Comando para flashear**:
    ```bash
    openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program build/Nucleo_F413_Template.elf verify reset exit"
    ```

---

## 📂 Detalles Técnicos
- **Microcontrolador**: STM32F413ZHT6
- **Drivers**: STM32 Low-Layer (LL) para máxima eficiencia y control.
- **Script de Enlazado**: `STM32F413XX_FLASH.ld` configurado para 1.5MB Flash y 320KB SRAM.

---
*Parte del repo [Embedded C Training](https://github.com/julian-duque-alayon/Embbeded_C_Training)*
