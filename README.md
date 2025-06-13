# VSDIAT-openlane
Sky130 Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
# **VSDIAT Openlane Sky130 Workshop**
## **Sky130 Day1- Inception of open-source EDA, OpenLANE and Sky130 PDK  **
     
## **How to talk to computers**
### **0- Introduction to QFN-48 Package, chip, pads, core, die and IPs**
![WhatsApp Image 2025-06-12 at 8 38 49 PM](https://github.com/user-attachments/assets/f9946eff-3473-4318-a6d5-6e2e4049589b)


Arduino Board-it is the image of an arduino board ,the yellow cercile in it shows the chip,which controls the whole board. This chip is designed using a process called RTL to GDSII flow. Arduino includes both the hardware (the board) and software (the Arduino IDE) used to write and upload programs to the board.

![WhatsApp Image 2025-06-12 at 8 56 05 PM](https://github.com/user-attachments/assets/64b1bd30-eae2-40ae-8d31-5cf3598b58a3)


This diagram represents a block-level architecture of a Processor or SoC (System on Chip) and its interfacing components, focusing on the pinout and peripheral connections.This is a typical SoC interfacing diagram showing how various communication interfaces (I2C, UART, QSPI), memory (SDRAM, Flash, EEPROM), and power lines are connected around the Processor/SoC. It's useful in embedded system design for understanding pin usage and functional blocks.
![WhatsApp Image 2025-06-12 at 8 38 49 PM (1)](https://github.com/user-attachments/assets/46121903-7a16-41bf-b19c-7f9be63cb643)
![WhatsApp Image 2025-06-12 at 8 38 49 PM (2)](https://github.com/user-attachments/assets/2678b7b9-ccbb-4246-8572-998878c73bb2)
![WhatsApp Image 2025-06-12 at 8 38 51 PM (1)](https://github.com/user-attachments/assets/ca8959ca-e572-4ba3-9c70-735aa49de9b6)



components of chip
1)pads :it can send the signals inside the chip and vice versa

2)core :place where digital logic gates are placed in

3)die :size of the entire chip manufactured on silicon paper

![WhatsApp Image 2025-06-12 at 8 38 51 PM (3)](https://github.com/user-attachments/assets/081eba33-fe35-4c61-856d-fe5332e73256)


This image shows the top-level layout of a System-on-Chip (SoC) design based on the RISC-V architecture, which includes a variety of blocks used in integrated circuit (IC) design. This layout helps VLSI designers understand how the digital logic, analog IPs, and I/O interfaces are arranged on the chip. It is part of the physical design or floorplanning process in chip design.
A typical chip consists of RISCV SoC,SRAM,dac,adc0,adc1,PLL,SPI,gpiobank; in that SRAM,dac,adc,PLL are Foundry IP's and the rest are Macros.
Foundry IPs and macros are pre-designed, verified blocks provided by semiconductor foundries (like TSMC or GlobalFoundries) that include essential components such as memory, I/O cells, PLLs, and standard cells, used to speed up and standardize chip design.
A** Foundry** in chip design refers to a company that manufactures semiconductor chips (like processors) based on designs provided by other companies.
Examples: TSMC, Samsung Foundry, GlobalFoundries.
These foundries do not design chips—they only fabricate them.

**IP** stands for **Intellectual Property.**
It refers to pre-designed, reusable blocks of logic or functions, like processors, memory controllers, USB interfaces, etc., that can be integrated into a chip to save time and effort during development.

**Macros** are large, pre-designed blocks such as memory units (like SRAM), analog blocks, or I/O blocks, which are placed as fixed (hard) components during physical layout.

## **  1- Introduction to RISC-V**

RISC-V is an open-source instruction set architecture (ISA) developed at the University of California, Berkeley. The “V” stands for the fifth generation of RISC designs. Unlike other ISAs, RISC-V is free to use and doesn't require licensing fees. Many companies now support RISC-V, and it works with popular operating systems and software tools.

RISC-V instructions are mainly 32-bit in size, but it also supports longer instructions for advanced features. It has versions for 32-bit, 64-bit, and even 128-bit address spaces, though the 128-bit version is still experimental. In hardware, the chip is connected to its package using bond wires.

![WhatsApp Image 2025-06-12 at 9 22 37 PM](https://github.com/user-attachments/assets/f4a27248-3fda-42e3-8e3a-7715d1442614)


Instruction Set Architecture(ISA):it is the language of the computer(how we talk to the computer)
That is the C program compile to RISCV assembly language program and then convert it to machine language(Binary language) and it execute in the layout of the chip and we get the output.

## **2-From Software Applications to Hardware**
