# VSDIAT Openlane Sky130 Workshop
### Sky130 Day1- Inception of open-source EDA, OpenLANE and Sky130 PDK  
     
## How to talk to computers
## 0- Introduction to QFN-48 Package, chip, pads, core, die and IPs
![WhatsApp Image 2025-06-12 at 8 38 49 PM](https://github.com/user-attachments/assets/f9946eff-3473-4318-a6d5-6e2e4049589b)


Arduino Board-it is the image of an arduino board ,the yellow circle in it shows the chip,which controls the whole board. This chip is designed using a process called RTL to GDSII flow. Arduino includes both the hardware (the board) and software (the Arduino IDE) used to write and upload programs to the board.

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

A **Foundry** in chip design refers to a company that manufactures semiconductor chips (like processors) based on designs provided by other companies.
Examples: TSMC, Samsung Foundry, GlobalFoundries.
These foundries do not design chips—they only fabricate them.

**IP** stands for **Intellectual Property.**
It refers to pre-designed, reusable blocks of logic or functions, like processors, memory controllers, USB interfaces, etc., that can be integrated into a chip to save time and effort during development.

**Macros** are large, pre-designed blocks such as memory units (like SRAM), analog blocks, or I/O blocks, which are placed as fixed (hard) components during physical layout.

##   1- Introduction to RISC-V

RISC-V is an open-source instruction set architecture (ISA) developed at the University of California, Berkeley. The “V” stands for the fifth generation of RISC designs. Unlike other ISAs, RISC-V is free to use and doesn't require licensing fees. Many companies now support RISC-V, and it works with popular operating systems and software tools.

RISC-V instructions are mainly 32-bit in size, but it also supports longer instructions for advanced features. It has versions for 32-bit, 64-bit, and even 128-bit address spaces, though the 128-bit version is still experimental. In hardware, the chip is connected to its package using bond wires.

![WhatsApp Image 2025-06-12 at 9 22 37 PM](https://github.com/user-attachments/assets/f4a27248-3fda-42e3-8e3a-7715d1442614)


Instruction Set Architecture(ISA):it is the language of the computer(how we talk to the computer)
That is the C program compile to RISCV assembly language program and then convert it to machine language(Binary language) and it execute in the layout of the chip and we get the output.

## **2-From Software Applications to Hardware**


Here we discuss about the applications run on a system
The process is
![WhatsApp Image 2025-06-13 at 10 35 34 PM](https://github.com/user-attachments/assets/8c02b8bb-4f10-4f0c-8bd4-43bea1770b70)

here the application softwares like word,powerpoint etc: enters to system software ,there it converts application program to binary language.
The system software has three layers:

**1) Operating System(OS)**: it handles IO operations and allocate memory  also it manage the low level system functions.It takes the application to assembly language program to binary language program which is understood by the hardware.

**2) Compiler**:It takes the output from the operating system as C,C++,Java and convert them into intsructions. These instructions depends upon hardware.

**3) Assembler**: it converts the instruction in the compiler to binary language(machine language).And then this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.
 Example:
 ![WhatsApp Image 2025-06-13 at 10 35 35 PM](https://github.com/user-attachments/assets/3cd39e5a-2418-49bd-9862-417eb9d9b039)
 

 This image shows how a stopwatch application works from high-level code to hardware execution. A C program (shown in the center) is written to implement stopwatch functionality, which is then compiled by system software (like Windows or Linux) into machine instructions. These are further translated into RISC-V assembly code, which the hardware (chip layout) can understand and execute, producing the final stopwatch output.

 ![WhatsApp Image 2025-06-13 at 10 35 35 PM (1)](https://github.com/user-attachments/assets/c97254ab-d9ce-4f7f-9bcb-04c162b1844e)


This image explains how a high-level instruction like add x6, x10, x6 is processed down to the hardware level. The assembler converts this instruction into binary machine code based on the computer's Instruction Set Architecture (ISA). This binary is understood by the Register Transfer Level (RTL) design, which is then synthesized into a netlist. Finally, the netlist undergoes physical design to generate the chip layout that is implemented as real hardware capable of executing such instructions.
 

## SoC design and openlane
## 3-Introduction to all components of openlane digital ASIC design

![WhatsApp Image 2025-06-13 at 10 59 12 PM](https://github.com/user-attachments/assets/c32247df-4ecf-420d-969a-efa316c326e2)

This image provides an overview of the Open Source Digital ASIC Design flow using tools and data from open communities. At the center is ASIC (Application-Specific Integrated Circuit), which is designed using the combination of EDA tools,RTL designs, PDK data.

**1) EDA tools**: (Electronic Design Automation), such as QFlow, OpenROAD, and OpenLANE.it is used to design and verify PCB and IC.

**2) RTL designs**: (Register Transfer Level), sourced from platforms like librecores.org, opencores.org, and GitHub.

**3) PDK data**:PDK = Process Design Kit
 It is a Collection of files used to model a fabrication process for the EDA tools used to design an IC
  > Process Design Rules: DRC, LVS, PEX
  > Device Models
  > Digital Standard Cell Libraries
  > I/O Libraries
  PDK Data (Process Design Kits), such as the FOSS 130nm Production PDK developed by SkyWater and Google.

![WhatsApp Image 2025-06-13 at 11 13 32 PM](https://github.com/user-attachments/assets/9374210d-e3c3-4ace-86ba-ff9fb58e7c60)


Intel’s Pentium 4 Extreme Edition (P4EE) achieved 3.46 GHz clock speed using the 130nm process back in Q4 2004, proving that high speeds are possible at this node.
The Oklahoma State University (OSU) team achieved 327 MHz post-layout clock frequency for a single-cycle RV32i RISC-V CPU using a 130nm process.
A pipelined version could exceed 1 GHz, further demonstrating the node’s capability.


## 4-Simplified RTL2GDS flow

![WhatsApp Image 2025-06-13 at 11 19 23 PM](https://github.com/user-attachments/assets/177ae6d6-530f-4100-9537-57e9bba520f0)

![WhatsApp Image 2025-06-13 at 11 55 06 PM](https://github.com/user-attachments/assets/5af98f48-3acc-43e6-8c67-06a09281c3e8)


It shows a simplified RTL (Register Transfer Level) to GDSII (Graphic Data System II) flow, which is a standard process in digital chip design. The flow starts from the RTL description of a circuit and ends with the final layout file used for manufacturing. The steps include: Synthesis (converting RTL to a gate-level netlist), Floorplanning and Power Planning (FP+PP) (defining block placement and power structure), Placement (arranging cells on the chip), Clock Tree Synthesis (CTS) (designing the clock signal distribution network), Routing (connecting all elements with metal wires), and Sign-Off (final checks for timing, power, and design rules). The PDK (Process Design Kit) provides technology-specific information used throughout these steps. This flow is crucial for transforming high-level designs into manufacturable silicon chips.
In detail:
**Step 1: Synthesis**: it converts RTL to a circuit out of compoents from the standard cell library(SCL)

**SCL**:standard cell library: Standard cells have regular layout ,each has different views or models; 
> electrical,HDL,SPICE
> Layout(abstract and detailed)

![WhatsApp Image 2025-06-14 at 12 17 09 AM](https://github.com/user-attachments/assets/f7d0c01e-a423-4353-a2b3-ab0e688679ea)


**Step 2: Floor/Power planning** : The main objective of floorplanning or power planning in the RTL to GDSII flow is to organize and allocate space efficiently on the chip for various functional blocks, while ensuring proper power distribution and connectivity.

**chip foor planning**: partition the die between different system building blocks and place the I/O pads.

![WhatsApp Image 2025-06-14 at 12 17 11 AM](https://github.com/user-attachments/assets/31beb50b-f227-4528-9383-4d9d7c91c66b)


**Macro floor planning**: it is the process of placing large pre-designed blocks (macros), such as memory or IP cores, on the chip layout in an optimal way to minimize area, improve performance, and ease routing congestion. 

![WhatsApp Image 2025-06-14 at 12 17 11 AM (1)](https://github.com/user-attachments/assets/32b9338a-552f-471d-8dba-4bd447e2aed9)


**Power planning**: it is the process of designing a power distribution network to ensure reliable and efficient delivery of power to all parts of the chip.

![WhatsApp Image 2025-06-14 at 12 07 06 AM](https://github.com/user-attachments/assets/312d4f70-a273-43ec-a80d-6fab3192a951)


**Step 3: Placement** :Place the cells on the floorplan rows ,aligned with the sites.usually done in 2 steps:
    1.Global: to find positions for cells,cells may be overlapped
    2.Detailed: positions from global are minimally altered.

![WhatsApp Image 2025-06-14 at 12 17 10 AM](https://github.com/user-attachments/assets/02357cba-7048-40f8-afdf-f83436b4af90)


**Step 4: Clock Tree Synthesis** :it creates a clock distribution network,it helps to deliver the clock to all sequential elements(eg:FF) with minimum skew and in a good shape usually a tree(H,X...).
It  is the stage where the clock signal is distributed to all flip-flops in a balanced manner.The goal is to minimize clock skew and latency to ensure synchronous operationSpecial buffers and inverters are inserted to drive the clock signal across the chip.CTS helps meet timing constraints like setup and hold time.A well-designed clock tree ensures reliable and predictable chip performance.


![WhatsApp Image 2025-06-14 at 12 17 10 AM (1)](https://github.com/user-attachments/assets/d5acace5-f28f-4fc6-9a59-be8143e0a676)


**Step 5: Routing** :implement the interconnect using the available metal layers.metal tracks form a routing grid and it is huge.it connects all the placed cells based on the netlist using metal layers.
It includes signal routing (connecting logic) and power routing (VDD and GND lines).Routing is done in two steps: global routing (path planning) and detailed routing (exact wire placement).Proper routing avoids congestion, crosstalk, and ensures timing closure.The final routed design is essential for generating the GDSII layout for fabrication.

![WhatsApp Image 2025-06-13 at 11 55 08 PM](https://github.com/user-attachments/assets/7fd57a7d-4340-49ff-bc97-ac63b1bc1e6c)



**Step 6: Sign off** :ignoff is the final stage in the chip design flow where the design is thoroughly checked for correctness and readiness for fabrication.It includes critical checks like timing analysis, power analysis, signal integrity, DRC (Design Rule Check), and LVS (Layout vs. Schematic).These checks ensure the design meets all functional, electrical, and physical requirements.


## 5-Introduction to OpenLane and Strive chipsets

OpenLANE is an open-source, automated flow that converts a digital design (written in RTL) into a physical chip layout (GDSII format) using a collection of tools like OpenROAD, Yosys, Magic, Netgen, and others. It is designed to run without human help in between steps (no-human-in-the-loop), and its main goal is to create a "clean" GDSII — meaning the final layout has no errors in layout vs. schematic (LVS), no design rule check (DRC) violations, and no timing issues. OpenLANE supports the SkyWater 130nm open PDK and is used to create SoCs (System-on-Chips) through a fully open-source environment. The striVe family of SoCs was built using OpenLANE and includes different versions with various RAM configurations and design modules.

OpenLANE supports two operation modes: Autonomous, where everything runs automatically with a push of a button, and Interactive, where each design step is done manually for better control and learning. It includes 43 example designs, each with optimal settings, to help users understand and experiment with the design flow. The striVe SoC family includes variants like striVe 1, 2, 2a, 3, 5, and 6, each offering different memory setups and testing features. Overall, OpenLANE makes chip design more accessible, especially for students and researchers, by offering a complete and open platform from RTL to GDSII.

## 6-Introduction to OpenLane and detailed ASIC design FLOW

## Get familiar to open-source EDA tools
