# 🚀 Week 1: Data Anatomy and Memory Map

Let's get to work. This first week is designed to turn the theory you've been reading into **muscle memory**. Professional firmware development isn't just about understanding concepts—it's about applying clean code principles and getting comfortable with the hardware from day one.

> [!IMPORTANT]
> **LeBlanc's Law:** *"Later equals never"*.  
> Don't leave for tomorrow what you can program today.

---

## 🏆 The Big Weekly Goal: "The LED Carry Calculator"
By Sunday, you must have programmed a system that:
1. **Critical Operation:** Performs an arithmetic operation (such as an addition) that causes a bit overflow (**Integer Overflow**).
2. **Visualization:** Configures the physical registers of the **STM32F413ZH** to display the result in binary using the onboard LEDs (**PB0, PB7, PB14**).
3. **Low-Level:** Handles the hardware using **direct memory pointers** and the `volatile` qualifier, without using any external ST libraries.

---

## 📅 Daily Programming Plan (Atomic Level)

| Day | Programming Objective (Task) | Expected Result |
| :--- | :--- | :--- |
| **Monday** | Create the `printStandardTypeSizes` function using exclusively `<stdint.h>`. | See the exact size of `uint8_t`, `uint32_t`, and `float` in the console. |
| **Tuesday** | Print memory addresses of a global and a local variable using `%p`. | Confirm that the global variable starts at `0x20...` (SRAM) and the local one on the Stack. |
| **Wednesday** | Implement bitwise operation macros (`SET_BIT`, `CLEAR_BIT`) and test them. | Master surgical bit manipulation before touching the hardware. |
| **Thursday** | Write code that reads the `RCC_AHB1ENR` register (address `0x40023830`). | Validate access to physical addresses using pointer casting. |
| **Friday** | **Physical Workshop:** Configure LED pins as output and perform the addition with overflow. | See the result of your C logic physically reflected in the board's voltages. |

---

## 🧐 Why should you program today?
Procrastination is the first obstacle for an architect. The book *Clean Code* explains that learning to write clean code requires sweating over it and practicing it yourself. Reading the manual is necessary, but if you don't program, you will only be accumulating **"airplane knowledge"** that you'll forget upon landing.

### 🏁 Your technical goal for today:
**Don't finish the day without your Makefile/CMake compiling a `main.c` that uses `sizeof()` to validate that you are on a 32-bit architecture.** That small dopaminergic victory is what will eliminate procrastination for tomorrow.

---

## 🛠️ Quick Start Guide

### 1. Build the Project
```bash
# Configure the build system
cmake -B build -G Ninja -DCMAKE_TOOLCHAIN_FILE=cmake/stm32_gcc.cmake

# Compile
cmake --build build
```

### 2. Flash the Board
```bash
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c "program build/Nucleo_F413_Template.elf verify reset exit"
```

---
*Back to [STM32 Modules](../README.md)*
