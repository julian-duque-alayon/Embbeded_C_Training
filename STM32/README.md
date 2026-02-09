# 📡 STM32 Projects

Repository section dedicated to development with **STM32** microcontrollers. This directory contains templates and projects for various STM32 boards.

---

## �️ General Hardware Workflow (WSL Support)

All STM32 boards in this repository use **ST-LINK** for debugging and flashing. Since hardware is connected via USB to Windows but we use WSL for development, follow these universal steps:

### 1. Windows Side (PowerShell)
Expose the USB debugger to WSL:
1. **Identify the BUSID**:
   ```powershell
   usbipd list
   ```
2. **Attach to WSL**: (Automates reconnection if device resets)
   ```powershell
   usbipd attach --wsl --busid <YOUR_BUSID> --auto-attach
   ```

### 2. WSL Side (Linux Terminal)
Verify the connection:
```bash
lsusb
# Look for "STMicroelectronics ST-LINK"
```

---

## 📂 Sub-Projects & Templates

- **[Template_NucleoF413ZH](./Template_NucleoF413ZH)**: Clean project base for the Nucleo-144 board (Cortex-M4).
- *(Add more boards/projects here in the future)*

---

## 💡 Troubleshooting
- **Connection Lost**: If flashing fails, check `lsusb` again. You might need to re-run the `usbipd attach` command in PowerShell.
- **Permission Denied**: If OpenOCD cannot open the device, ensure your user has permissions for the plugdev group or use `sudo`.

---
*Back to [Main Repository](../README.md)*
