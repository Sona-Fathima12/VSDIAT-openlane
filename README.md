# VSDIAT Openlane Sky130 Workshop
# Sky130 Day1- Inception of open-source EDA, OpenLANE and Sky130 PDK  
     
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

##   Introduction to RISC-V

RISC-V is an open-source instruction set architecture (ISA) developed at the University of California, Berkeley. The “V” stands for the fifth generation of RISC designs. Unlike other ISAs, RISC-V is free to use and doesn't require licensing fees. Many companies now support RISC-V, and it works with popular operating systems and software tools.

RISC-V instructions are mainly 32-bit in size, but it also supports longer instructions for advanced features. It has versions for 32-bit, 64-bit, and even 128-bit address spaces, though the 128-bit version is still experimental. In hardware, the chip is connected to its package using bond wires.

![WhatsApp Image 2025-06-12 at 9 22 37 PM](https://github.com/user-attachments/assets/f4a27248-3fda-42e3-8e3a-7715d1442614)


Instruction Set Architecture(ISA):it is the language of the computer(how we talk to the computer)
That is the C program compile to RISCV assembly language program and then convert it to machine language(Binary language) and it execute in the layout of the chip and we get the output.

## From Software Applications to Hardware


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


## Simplified RTL2GDS flow

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


## Introduction to OpenLane and Strive chipsets

OpenLANE is an open-source, automated flow that converts a digital design (written in RTL) into a physical chip layout (GDSII format) using a collection of tools like OpenROAD, Yosys, Magic, Netgen, and others. It is designed to run without human help in between steps (no-human-in-the-loop), and its main goal is to create a "clean" GDSII — meaning the final layout has no errors in layout vs. schematic (LVS), no design rule check (DRC) violations, and no timing issues. OpenLANE supports the SkyWater 130nm open PDK and is used to create SoCs (System-on-Chips) through a fully open-source environment. The striVe family of SoCs was built using OpenLANE and includes different versions with various RAM configurations and design modules.

OpenLANE supports two operation modes: Autonomous, where everything runs automatically with a push of a button, and Interactive, where each design step is done manually for better control and learning. It includes 43 example designs, each with optimal settings, to help users understand and experiment with the design flow. The striVe SoC family includes variants like striVe 1, 2, 2a, 3, 5, and 6, each offering different memory setups and testing features. Overall, OpenLANE makes chip design more accessible, especially for students and researchers, by offering a complete and open platform from RTL to GDSII.

## Introduction to OpenLane and detailed ASIC design FLOW

![WhatsApp Image 2025-06-14 at 1 42 15 PM](https://github.com/user-attachments/assets/20fee7e6-7022-4f11-b150-4aabfc7d5402)


OpenLANE includes a design exploration utility that is also used for regression testing. In this process, OpenLANE is run on around 70 designs to make sure everything is working correctly. The results are compared with the best-known previous results to confirm that recent changes have not caused any performance or quality issues.

Design for Test (DFT) is a step that ensures the chip can be tested after manufacturing. It includes several tasks such as scan insertion, automatic test pattern generation, pattern compaction, fault coverage measurement, and fault simulation. These help in detecting defects in the final silicon chip.

After DFT, physical implementation is done using the OpenROAD tools. The major steps include floor and power planning, adding decoupling capacitors and tap cells, global and detailed placement of components, post-placement optimization, clock tree synthesis (CTS), and global and detailed routing. These steps physically arrange and connect the circuit on the chip.

Since CTS and post-placement optimization change the netlist, it is important to verify that the design's logic remains the same. This is done using the LCE tool in Yosys, which performs formal verification to ensure that the functional behavior has not changed due to netlist modifications.

![image](https://github.com/user-attachments/assets/89db5fe6-2621-446a-8bf1-ec3343e12c7b)
![image](https://github.com/user-attachments/assets/73630be3-8bc6-4ab6-94db-6112c8be4491)
![image](https://github.com/user-attachments/assets/d68dfe39-8c76-413c-ad85-776b1e12b384)


During chip fabrication, metal wires can act as antennas and collect charge, which may damage transistor gates. This is called an antenna rule violation. To fix it, we can either bridge the wire to a higher metal layer or add antenna diode cells to release the charge. OpenLANE uses a preventive method by placing fake antenna diode cells next to every cell input after placement. If the antenna checker detects a real violation, these fake diodes are replaced with actual diode cells.

Static Timing Analysis (STA) checks if the chip design meets timing requirements. This involves extracting resistance and capacitance information from the layout using DEF2SPEF, then running STA with the OpenSTA tool. Any timing violations are reported for correction.

Finally, physical verification is performed. Design Rule Checking (DRC) ensures the layout follows manufacturing rules, which is done using Magic. Layout Versus Schematic (LVS) checks that the physical layout matches the circuit logic. This is done using Magic and Netgen, and a SPICE netlist is also extracted from the layout for further analysis.


## Get familiar to open-source EDA tools
## OpenLANE directory structure in detail

cd : opens the particular folder

ls : lists the content of the folder

pwd : shows the present working directory

mkdir : to make a new directory

command --help : shows the complete use that command

clear : clears the terminal screen

## LAB DAY 1
### 1.Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
 > SCREENSHOTS OF LAB ATTACHED BELOW.

![Capture 1](https://github.com/user-attachments/assets/988cff17-cd43-49f5-9d02-a8e122852a16)
![Capture 2](https://github.com/user-attachments/assets/6d9dd368-b6ad-4e17-a867-aac3d12c86e9)

### 2.Calculate the flop ratio.

![Capture 3](https://github.com/user-attachments/assets/bf645a79-1d9f-486e-ac31-5410a15e15a3)

Flop ratio= no. of D flipflops/total no. of cells
          = 1613/14876
          = 0.1084296854
Percentage of DFF's =Flop ratio * 100
                    = 0.1084296854*100
                    = 10.84296854


# Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells
## Chip Floor planning considerations
## Utilization factor and aspect ratio
### 1.Define width and height of core and die.

![image](https://github.com/user-attachments/assets/7736bba5-e6d3-4963-bc13-163261792152)


SO, how to calculate height and width
lets begin with a netlist, basic netlist(connectivity between all of the components) used two flipflops(FF),and logic gates between them.

![image](https://github.com/user-attachments/assets/39211aff-63ff-4a41-a6d2-f1ace3ab2544)
![image](https://github.com/user-attachments/assets/0ce0dc7a-b2d4-4f21-8f25-3ba182c4aeff)


FF comes under the class of register/FF. And A1,O1 are standard cells.to find thw dimensions of chip we mostly depends on dimensions of logic gates(OR,AND) and FF.so consider both standard cells and FF has 1 unit height and width so there area is 1 sq unit.

lets calculate area occupied by the below netlist on a silicon waferwith these dimensions so we remove the wires and club them in a single plate.

![image](https://github.com/user-attachments/assets/93cd3938-2173-4a14-bc67-28eef8ac2657)


So, the fundamental logic or netlist has 4 sq unit. that is minimum area occupied by the netlist is 4 sq unit.
so we know that die encapsulates the core,piece of area where circuit is built therefore the circuit not exceed.we imprint these on a silicon wafer multiple times.

further calculations and theory:
![image](https://github.com/user-attachments/assets/c780dbf9-cff0-4fea-9400-bc282e3d2583)
![image](https://github.com/user-attachments/assets/b0e5d49e-c790-4453-9e47-d32ac4c1fb25)


here we need to understand two terms.utilisation factor and aspect ratio.So we have utilisation factor and aspect ratio equations here. So the clubbed flip flop and Gates together fixed in the  core area. So we can say that 100 percentage utilisation of core is there that is netlist is completely fit in the core part. So we can calculate the utilisation factor and applying values we get the utilization factor as 1 , ( 4 sq unit ÷ 4 Sq unit).Practically we go for 50 % or 60% utilisation factor with UF = 0.5 or 0.6 .Next is to calculate aspect ratio. The equation is given that is height / width  of core ,so applying values we get the aspect ratio as 1 here.By meaning the aspect ratio equal to 1 which means that square chip shape and if the aspect ratio is not equal to one then the chip shape will be  rectangle shape.

another example:
![image](https://github.com/user-attachments/assets/dd5519ac-b2a9-4f6f-94b2-19d6d23f8c6a)

## Concept of preplaced cells.
### 2. define location of pre place cells.

![image](https://github.com/user-attachments/assets/0fcab707-f9c2-475d-820c-f3585e1bdbb7)


So ,the output of the combinational  logic in the main circuit is a huge circuit which contains 100K gates maximum .so we divide this into 50K gates and 50K gates that is 2 blocks .So we divide this into 50K gates and 50K gates that is 2 blocks .

black box: the black box means that the inner section will be invisible if we look from the top so  divided gates can be black boxed, so we get 2 blocks. the advantages of black box is that if we use it in netlist multiple times we have to use this black boxes only it can be reused on the top netlist.These are implemented ones but can be used too many times.

similarly there are other IP also available in market that  similarly there are other IP also available in market ,example memory,Comparator., complex clock gating cell, Mux.
![image](https://github.com/user-attachments/assets/e6c7776f-6d6e-4613-b1bf-8922316c80ee)

### how do we find locations of preplaced cells.

![image](https://github.com/user-attachments/assets/40f5ff84-9a24-4eb6-9d6a-24bf863addb1)

lets say we have block a,b,c.so they arranged in a fashion that; 

1.IPs act as macros, often communicating with input/output (I/P) pins.

2.They should be placed close to the I/P side and in a way that their locations cannot be changed.

3.They should not touch any ecbores and their local areas should be well-defined.

4.Decoupling capacitors should surround them.

## Decoupling capacitor
###  3.Decoupling capacitor and why do we need it.

![image](https://github.com/user-attachments/assets/f4228c3b-9b86-43fa-8fe7-0e677d8d7b73)
![image](https://github.com/user-attachments/assets/6b3b3ead-5149-4e22-a562-d299e401afec)

when many gates switch at the same time, the power supply may not respond quickly enough, leading to voltage drops or noise on the power lines. This unstable power can cause incorrect logic behavior or timing issues in the chip. A decoupling capacitor stores small amounts of charge and quickly releases it when needed, helping to maintain a stable voltage level and protecting the circuit from power disturbances.

What is a Decoupling Capacitor?
It's a capacitor, often a large one, placed close to integrated circuits (ICs) or other components.
It acts like a small, local energy reservoir.
It's designed to provide a stable voltage supply.

![image](https://github.com/user-attachments/assets/70261ece-b5e0-4b13-91d5-8dab76fc52ca)


In chip design, a decoupling capacitor is needed to ensure a stable and clean power supply to the internal circuits. When many transistors switch at once, they draw a sudden burst of current, which can cause voltage fluctuations or noise on the power lines. A decoupling capacitor helps by temporarily supplying this needed current, reducing voltage dips and filtering out noise. It acts like a small energy reservoir placed close to the logic cells, ensuring the chip functions reliably even during high switching activity. Without decoupling capacitors, the chip may experience timing errors or even malfunction due to unstable power.

![image](https://github.com/user-attachments/assets/0591ef15-2df4-4568-add1-851833fd77b9)

## Power Planning
### 4.Power Planning

![image](https://github.com/user-attachments/assets/6125f51d-1233-463b-ac89-4a520caa8876)


Consider a scenario where a local circuitry block, treated as a black box, is repeated multiple times with some boundary logic. A signal is sent from a driver to a load, transitioning from logic 0 to logic 1. To ensure reliable communication, the signal line must consistently carry the correct signal from driver to load. Normally, a decoupling capacitor is used to supply quick bursts of current when needed, stabilizing the voltage during switching. This works well for localized areas.

However, in the case of a 16-bit bus, which needs to maintain consistent signals across all bits, placing decoupling capacitors everywhere is not practical. Since the power supply is located far from the bus, voltage drops naturally occur due to resistance in the path. Without nearby decoupling capacitors, the bus may not receive sufficient and stable voltage during transitions, risking signal integrity and reliability.

![image](https://github.com/user-attachments/assets/6f52897f-83cf-4e29-9897-34a2c2d3c5d5)
![image](https://github.com/user-attachments/assets/694e3e77-1b67-4d13-94a1-93e3189c8fc9)

These two figures illustrate issues that occur when multiple digital signals switch simultaneously on a bus without adequate local decoupling capacitors. In the first image, when several signals transition from logic high (V) to logic low (0), the corresponding capacitors must discharge through a common ground (Vss) tap point. This sudden current rush causes a temporary rise in the ground potential known as ground bounce, which can lead to incorrect logic level detection and signal integrity issues.

In the second image, signals transition from logic low (0) to logic high (V), causing several capacitors to draw current from the single power supply (Vdd) tap point. This sudden demand results in a temporary voltage drop at the Vdd node, known as voltage droop. Like ground bounce, voltage droop can cause functional failures due to insufficient voltage for proper logic level interpretation. Both effects highlight the importance of placing decoupling capacitors close to switching elements to maintain power integrity.

The solution of the problem is use multiple power supply. So, every block will take charge from neartest power supply and similarly dump the charge to the nearer ground. this type of power supply is called mesh.

![image](https://github.com/user-attachments/assets/8effd5c6-1509-4dd0-ba82-0dc9a90f2a20)

![image](https://github.com/user-attachments/assets/67b2f327-5c53-4ab4-ae07-fb7d71fcf106)



## Pin placement and logical cell placement blockage
### 5. pin placement

![image](https://github.com/user-attachments/assets/2b51e135-553d-4eb2-8612-e30ce759b49f)


Consider a design where two separate circuits operate on different clock domains: the first is driven by Clk1 and takes Din1 as input to produce Dout1 as output, while the second is driven by Clk2 with Din2 as input and Dout2 as output. Additionally, there are some pre-placed cells, including BlockA, which receives inputs from both Din1 and Din2, and BlockB, which takes Clk1 and Clk2 as inputs and generates a clock output signal, ClkOut. Overall, the design features four input ports—Din1, Din2, Clk1, and Clk2—and three output ports—Dout1, ClkOut, and Dout2


![image](https://github.com/user-attachments/assets/d2e2804a-fd2f-4979-ba44-2e7a3b0176ce)



The given design illustrates two data paths working across two clock domains. In the upper path, Din3 is fed to a flip-flop (FF1) clocked by Clk1, and its output is passed through a buffer (labeled 1) and an XOR gate before reaching a second flip-flop (FF2) clocked by Clk2, producing the output Dout3. In the lower path, Din4 is input to another FF1, this time clocked by Clk2. Its output is passed through a buffer (1), then through an AND gate (with another input from Block C), and finally through another buffer (2) into FF2 clocked by Clk1, resulting in Dout4. Block C interfaces between both paths and interacts with Clk1 and Din3, playing a role in synchronizing or processing signals between the two domains.

![image](https://github.com/user-attachments/assets/df9e7d0a-c22d-456a-b86a-9760367952c0)

The complete design now has six input ports: Din1, Din2, Din3, Din4, Clk1, and Clk2. It produces five outputs: Dout1, Dout2, Dout3, Dout4, and ClkOut. Each data path flows through flip-flops and logic gates, with Blocks A, B, and C managing signal and clock coordination. The connectivity between all components is described using VHDL or Verilog, and this is known as the 'Netlist'.

![image](https://github.com/user-attachments/assets/d30c892d-3d31-488c-813d-23ea516f1926)


We now place the netlist inside the core that was designed earlier and aim to fill the empty space between the core and the die using pin information. The frontend team is responsible for defining the netlist, including all input and output connections, while the backend team handles the physical placement of pins. Based on where the pins are placed, we need to position the preplaced blocks close to their respective input sources. This ensures efficient routing and better performance in the overall layout.


## LAB DAY 2

1.Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.

![Capture 5](https://github.com/user-attachments/assets/4e56f7f7-3232-4fa8-a609-4cb4e9b06535)
![Capture 6](https://github.com/user-attachments/assets/ebcc3d54-9f02-4fa0-a30c-2cebc0aa74b5)

2.Calculate the die area in microns from the values in floorplan def.

![Capture 7](https://github.com/user-attachments/assets/60e4a25f-d59f-4db6-9039-60903646d28e)

Area of die in microns = Die width in microns * die height in microns
1000 Unit Distance = 1 Micron
Die width in unit Distance = 660685 - 0 = 660685
Die height in unit Distance =671405 - 0 = 671405
Distance in microns = Value in unit Distance / 1000
Die width in microns = 660685 / 1000 = 660.685 Microns
Die height in microns = 671405 / 1000 = 671.405 Microns
Area of Die in microns = 660.685 × 671.405 = 443587.212425 Square Microns

3.Load generated floorplan def in magic tool and explore the floorplan.

### Floor plan def in magic

Commands used:
![Capture 8](https://github.com/user-attachments/assets/116d68da-9629-4173-b0be-cf27e9773d69)

![Capture 9](https://github.com/user-attachments/assets/8c1bdf84-c1e9-4e21-9ea7-c8bbd59120d9)

### equidistant tapcells 
![Capture 10](https://github.com/user-attachments/assets/a3143efa-5145-438a-ab81-74909988e2e9)

### Port layer as set through config.tcl
![Capture 11](https://github.com/user-attachments/assets/657a3a62-4f1c-4e1b-98de-da6a85eed42d)
![Capture 12](https://github.com/user-attachments/assets/f4a7f662-608c-41b3-b9a0-296241783ada)


![Capture 13](https://github.com/user-attachments/assets/1b4041ab-3018-4887-a3aa-155b0f717e25)
![Capture 14](https://github.com/user-attachments/assets/d8256061-17f3-407e-b5de-1aa6e45a72e2)
![Capture 15](https://github.com/user-attachments/assets/7319834b-2a9e-4bca-b4f5-bf5bb0694e95)

4.Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

![Capture 16](https://github.com/user-attachments/assets/4f7be799-0238-4043-879e-8905a599f35f)
![Capture 17](https://github.com/user-attachments/assets/8165d202-a0d9-4416-842d-feb74a117b93)




## Library binding and placement
## netlist bindind and initial place design
### placement and routing stage

 step 1: bind netlist with physical cells.

 In practically, while logic symbols like NOT and AND gates are shown with distinct shapes (e.g., triangle for NOT), in physical design, all gates and components are represented as rectangular boxes with specific width and height. Each element in the netlist, including flip-flops and logic gates, is assigned a physical shape and dimension to reflect its real-world layout. This standardization is necessary because symbolic shapes don’t exist physically—so everything is mapped to a box-shaped form to fit into the chip layout accurately.

 ![image](https://github.com/user-attachments/assets/a8f0de85-b172-46a4-aada-754d84aad7be)
![image](https://github.com/user-attachments/assets/6dcf5eac-396f-4a89-a18c-7424b768426f)

So it is called a library. It has weight and height of each cell. It has timing information of each Gates and required condition of each cells as well. There are two types of libraries based on the shape or size and timing information or delay information.and also the various flavours of same cells are also present.

step 2: placement in floorplan

![image](https://github.com/user-attachments/assets/5074a1b4-23a2-4a63-b69f-525f867b2e14)
![image](https://github.com/user-attachments/assets/5e115e54-f209-4159-b12f-b008fc67cdb9)


after every logic gate and flip-flop from the netlist is assigned a proper shape and size, the next important step is placing these components onto the chip floorplan. The floorplan already contains the defined input and output ports, the netlist describing connectivity, and the physical dimensions of each component. With all this information, we now have a physical representation of each gate, which allows us to start positioning them on the floorplan based on how they are connected logically.

During placement, it is important to ensure that the locations of preplaced cells remain unchanged. These preplaced blocks serve specific roles in the design and must not be moved or overlapped by other cells. Placement must be done carefully so that no cell is positioned over the existing preplaced cells, and all logic gates are placed in a way that maintains the required signal flow. This ensures that logical connections are preserved, timing constraints are met, and signal delays are kept minimal.

Initially, the placement is done in such a way that all gates are located close to their related input and output pins to support better performance. However, upon examining the layout, it is noticed that the distance between FF1 of Stage 4 and input Din4 is longer compared to others. This could potentially impact timing and delay. To address this, optimization of the placement is needed to reduce this distance, thereby improving the overall timing and efficiency of the circuit layout.

step 3:Optimize placment.

It is the solution to the problem of distance in placement area. So we use repeated repeaters are basically buffers that will recondition your original signal that will make a new signal which replicates the original signal and send it again .
As repeaters  increase area will be loss inside the core.The following pictures I attached are showing the repeaters used in the placement of each set of cells.

In the first set the distance between Din1 and FF 1 is less . The wirelength is less and therfore there is not that much resistance and we can directly connect them together and from ff1 to 1 same there is no any large wirelength so we can connect to the together and similarly 1 to 2 and 2 to FF 2 and ff 2 to Dout1 can be connected without any problem because it has  acceptable wire length and there is no any huge capacitance so they can connected.

![image](https://github.com/user-attachments/assets/a4e7759f-aab3-48e9-94cf-4417102eedcf)

In second set the distance for wirelength is huge. So the capacitance is very high. So we use 2 buffers called  repeaters.But in someparts there is no delay. That means from ff1  to ff2 there is no delay .and after that we can connect ff2 to Dout2

![image](https://github.com/user-attachments/assets/5cedc953-651a-45ca-bb45-fc1470d75cc3)

similar to stage 2, in Stage 3 also we required the buffer between gate2 and FF2.


![image](https://github.com/user-attachments/assets/3e93cc95-abbe-44ac-9cf1-e31f0fa11106)

In sEt 4, it is big tricky compared to the other three stages.So here the Din4 cant reach f f1 because of the pre placed cells so a buffer is set there so Din4 can reach the repeaters and then f f 1 and from ff1 to 1. and if we look 1 to 2, it cant be reached that easily because there is a huge distance. So a buffer is placed also we can see that the crisscross with the second set, so we can say that 4th set is in  metal 3 layer set 2 in metal 1 or 2 layer,3rd set in metal layer 4. So we have to check that what we have done is correct or not first. for that, We need to do a timing analysis by considering the ideal clocks and according to the data of analysis. We will understand that a placement is correct or not.
![image](https://github.com/user-attachments/assets/6ac084d3-08ac-4da2-a4d3-f060706968d2)


## Need for libraries and  characterization
step 1: logic synthesis: arrangeent of gates that will represent your orginal functionality that you have described usinf RTL.
step 2: floorplanning: we import the output of logic synthesis that is netlist and decide the size of core and die(depends on the number of gates present in the netlist).
step 3: Placement: logic cells are placed in chip
step 4: clock tree synthesis(CTS) : that will take care of clock which reach every clock points.
step 5: routing : routing means connecting all the components together with metal wires so that signals (data, control, power) can move correctly between them.
step 6: static timing analysis : to analyse what is setup time ,old time,what is the maximum achieval frequency.

one thing common accross all stages are gates or cells

## LAB DAY 2 (BALANCE)
5.Load generated placement def in magic tool and explore the placement.

Commands used:
![Capture 18](https://github.com/user-attachments/assets/5bd9de61-a3bc-4456-a9b2-12853fbb6ce8)
![Capture 19](https://github.com/user-attachments/assets/269048ed-c8bf-4404-97b5-2e79d192b4d7)
![Capture 20](https://github.com/user-attachments/assets/df167c0a-1627-4dbc-afb7-aa9f1c87579b)

## Cell design and characterization flow.
## input for cell design flow












# Sky130 Day 3 - Design library cell using Magic Layout and ngspice characterization

## Inception of layout CMOS fabrication process
## 16-Mask CMOS Process

CMOS technology is widely used in making integrated circuits. The 16-mask CMOS process uses a sequence of 16 photolithographic masks to pattern different layers of materials on the silicon wafer, creating the complete CMOS structure.

### 1.Selecting a Substrate

Most common substrate used is p type silicon substrate.it has high resistivity(~50ohms),doping level of 10^15 cm^-3 etc.substrate doping should be less than “well” doping. This substrate acts as the foundation for all further layers and device structures.

### 2.Creating Active Region for Transistor
(Place where u actually see P and N mos transistors)

![image](https://github.com/user-attachments/assets/96b9284f-3257-43f4-92ec-349594f0957d)


Here creates an Isolation between those pockets.for that grow silicon dioxide (40nm) in p type substrate. Deposited a layer of Si3N3 of 80 nm ,identify region of where we have to create the pockets deposit a layer of photorealism of 1um. mask is  a ffabrication term.it is used to protect that particular part in photoresist layer when exposed to UV light.

![image](https://github.com/user-attachments/assets/a87627fb-51bd-4102-b7af-19f51ae7fe32)


After that wash it out ,we get  this figure 
![image](https://github.com/user-attachments/assets/c7250c02-97fd-4e81-bfab-b7cba9ab22d1)
![image](https://github.com/user-attachments/assets/b58aacfa-3752-4db3-ab65-00388154da3f)

Then remove the mask and photoresist layer to grow the oxides on the other areaSo we put it in an Oxidation furnace (high temperature  9000 degree celcius)it helps to grow the oxide in other area.if we do LOCOS (local oxidation of silicon) process, the exposed sio2 part will grow and bird break also form. This grown sio2 will provide the perfect isolation between two PMOS and NMOS. This is how we protect two transistor communicating with each other.  Next step is to remove the Si3N4 using hot phospheric acid.
![image](https://github.com/user-attachments/assets/1c7e1b90-8a2a-4003-bb4f-58e2419b1181)
![image](https://github.com/user-attachments/assets/573a88e4-ff82-431f-86d3-d31429185c22)



### 3.N-Well and P-Well Formation

![image](https://github.com/user-attachments/assets/4168103e-9fa6-4d9c-b64f-9709f38bdeb6)
![image](https://github.com/user-attachments/assets/b6dc7d02-c57f-4553-b568-c36565433099)


Through ion implantation, regions are doped to create n-wells (for PMOS) and p-wells (for NMOS) inside the substrate. This is often done using separate masks.

Here ,we need to protect one area while we create the transistor. Same steps come over here we use mask 2 here.after the process (same as above) we remove the mask and create a p well that is boron is diffused in ptype substrate using a process called ion implantationso it creates a p well and the energy required is similar to 200keV. Boron penetrates oxide layer and it enters to the active area creating p well

![image](https://github.com/user-attachments/assets/e7e8cec5-2534-42a4-b065-d9529616f94b)
![image](https://github.com/user-attachments/assets/b57f6b90-a4b8-46e4-b463-6b258df86552)


Similar for n well, Mask 3 is used and phosphorus is penetrative through oxide layer and creates n well with ion implantation.Phosphorus is bit heavier than boron so it’s energy is high.

![image](https://github.com/user-attachments/assets/d5731377-e8d8-44b2-8a09-7a74d96b302a)


Next we have to diffuse well so it has to occupy almost half of substrate area.now take the whole substrate in to the high temperature furnace (drive in furnace) put in high temperature and for too long time say 1100 degree celcius for 4 to 6 hours  and it creates yhe clear well.it is alled twin tub process.


### 4.Create a Gate

![image](https://github.com/user-attachments/assets/4faeca56-0ca6-4c64-a7bf-00aafdf018b3)


The gate terminal is the most important part of both PMOS and NMOS transistors because it controls whether the transistor turns on or off. This control is based on something called the threshold voltage—the voltage at which the transistor starts to conduct.The threshold voltage depends on a few things, especially the doping concentration and the oxide capacitance under the gate. So, before building the full gate structure, we first adjust the doping in that region.To do this, we use Mask 4 to mark the area, and then we perform ion implantation using boron ions (for p-type doping). These ions are implanted at a low energy level (around 60 keV) to precisely control the doping near the gate.A thin gate oxide layer is grown, and a polysilicon layer is deposited and patterned to form the gate. The gate acts as a control switch for the transistor.

Same process we will repeat for N-well also by using mask 5 and Arsenic ion.
![image](https://github.com/user-attachments/assets/4a23dc20-ea32-4986-8fe8-90e5d2f6abaf)
![image](https://github.com/user-attachments/assets/8ebc925d-b9f9-4cb6-8489-0cea945409eb)


The next important step is to form a clean and high-quality oxide layer for the gate. But before we do that, we need to remove the existing oxide layer, because it may have been damaged during earlier steps like ion implantation.

![image](https://github.com/user-attachments/assets/7213b2ee-4b71-4121-b589-31e50b348869)
![image](https://github.com/user-attachments/assets/e7b05ce9-4fa4-44e5-ab95-175d4ebe6f78)


To remove the damaged oxide, we use a chemical solution of HF (hydrofluoric acid). After cleaning, we grow a fresh oxide layer on the surface. This new layer has the same thickness but is much better in quality, which is important for reliable transistor operation.After that, we deposit a layer of polysilicon on top of the new oxide. This polysilicon contains extra impurities to reduce its electrical resistance, making it a good material for the gate terminal.Finally, we use Mask 6 along with photoresist to etch and shape the polysilicon, leaving it only where the gate should be.After etching, remove the photoresist and gate terminal looks like,


### 5. Lightly Doped Drain (LDD) Formation



In this step, we shape the doping near the gate to protect the transistor from unwanted effects like:

1.Hot electron effect
2.Short channel effect
For PMOS, we need a P+, P−, and N doping profile.
For NMOS, we need an N+, N−, and P doping profile.
So we do light ion implantation:
In the P-well (for NMOS), we use Mask 7 and implant phosphorus to create N− regions.

![image](https://github.com/user-attachments/assets/85602c26-016f-47a1-931b-d1dcce523154)
![image](https://github.com/user-attachments/assets/393d04bf-4aab-4f95-9b34-66d01237dd2f)



In the N-well (for PMOS), we use Mask 8 and implant boron to create P− regions.

![image](https://github.com/user-attachments/assets/9d9f4ec5-8649-4c16-a34d-8ecbecc7340d)
![image](https://github.com/user-attachments/assets/6f8da676-048c-4f64-9366-a657b7e6f8a6)

To protect these lightly doped regions, we form spacers beside the gate.We deposit a thick layer of SiO₂ or Si₃N₄ over the gate and then use plasma anisotropic etching to form the sidewall spacers.These spacers help define and shield the area during the next heavy doping step.


### 6.Source and Drain Formation


![image](https://github.com/user-attachments/assets/10521067-0638-4abf-92c3-04fcc4cfcc7f)


Now we create the source and drain of the transistors.First, we deposit a thin screen oxide layer. This layer helps avoid ion channeling during implantation.
Then we do heavy ion implantation:
In the P-well (PMOS):


![image](https://github.com/user-attachments/assets/ac487559-b5f8-43d8-b4af-755897a3e20f)
![image](https://github.com/user-attachments/assets/f71bac29-0bc7-43a6-8101-d0d5b25dabf9)


Use Mask 9 and implant arsenic ions at around 75 keV for N+ regions.



In the N-well (NMOS):

Use Mask 10 and implant boron ions at around 50 keV for P+ regions.

![image](https://github.com/user-attachments/assets/70fcf727-09e6-4ab3-871d-3922cb28ef7b)
![image](https://github.com/user-attachments/assets/37c802eb-1e0c-420f-816c-588c1a6ec445)



Next, we perform high-temperature annealing at about 1000°C.This causes the implanted regions to become the final source and drain, completing the transistor structure.

![image](https://github.com/user-attachments/assets/f1569fac-aea4-4c00-97ac-ee4520832024)


### 7. Contact and Local Interconnect Formation


First, we remove the thin screen oxide layer using etching.

![image](https://github.com/user-attachments/assets/10cc0f6f-4cbb-4875-9990-31a1210fbe32)


Then we deposit a titanium (Ti) layer using sputtering. Titanium is chosen because it has low resistivity.

![image](https://github.com/user-attachments/assets/dc4c8f42-1d35-4e12-a3fe-90730a080427)



Now, to form a good connection between Ti and the source, drain, and gate, we heat the wafer to 650–700°C in a nitrogen (N₂) atmosphere for about 60 seconds.This causes a chemical reaction, forming:Titanium silicide (TiSi₂) over silicon (to reduce contact resistance)Titanium nitride (TiN) over other areas (used for local interconnect)

![image](https://github.com/user-attachments/assets/22ff06ca-1a51-4f82-8d81-4c01c3726aa0)



Next:
![image](https://github.com/user-attachments/assets/252c331c-1c6f-4556-ae58-8d5f6d5e9bcc)



Use Mask 11 and photoresist to etch the TiN layer, forming precise contact openings.TiN is removed using RCA cleaning, and the local interconnects are formed.


### 8. Higher-Level Metal Formation


![image](https://github.com/user-attachments/assets/6a87594f-b3ce-4332-bbe5-c13fb22289d1)
![image](https://github.com/user-attachments/assets/0659b537-30e2-4d85-9ace-64041d7dcc41)

This stage forms the upper metal layers that connect different parts of the chip.
First, we observe that the wafer surface is not flat, which causes issues during metal deposition.
To solve this, we deposit a thick SiO₂ layer (doped to lower resistivity), and perform CMP (Chemical Mechanical Polishing) to flatten the surface.





Now, for the metal contacts:

Use Mask 12 and photoresist to etch openings in SiO₂.

![image](https://github.com/user-attachments/assets/1acffc5b-2e0f-47f0-9d0b-8c56acf96127)

Deposit a thin layer of TiN (~10 nm). This layer:

![image](https://github.com/user-attachments/assets/680fea18-67ba-4fbf-9e58-90cd741a801c)


Acts as a barrier between silicon and metalHelps adhesion between metal and oxide.Next, deposit a blanket layer of tungsten (W) to fill the holes.

![image](https://github.com/user-attachments/assets/e0e07c0f-8230-4c94-83bc-c5ab3cf0e3fb)

Again, use CMP to planarize the surface. Now, W acts as the contact plug.

![image](https://github.com/user-attachments/assets/4eb1dc38-e3a2-4b46-a9f5-aed4c0d5b58b)



To form the first-level metal interconnects:Deposit aluminum (Al) layer.Use Mask 13 and photoresist to etch Al, creating the metal paths using plasma etching.

![image](https://github.com/user-attachments/assets/3b7ac1ec-805c-4eef-9a08-2c2a32bb2a92)

![image](https://github.com/user-attachments/assets/1a1fc989-1c26-48b9-a6b7-296450217f53)


For the second metal layer.Repeat similar steps using:

Mask 14 to etch SiO₂
![image](https://github.com/user-attachments/assets/87e5a023-3eb6-4532-aa56-85befb367b77)
![image](https://github.com/user-attachments/assets/0fa93393-198f-4f3f-b1c8-dfa2b6472668)
![image](https://github.com/user-attachments/assets/97c1f0a2-2a1f-4a25-a571-cbd23dcff1b4)

Mask 15 to etch the second Al layer

![image](https://github.com/user-attachments/assets/4c7e3085-7250-4598-922d-ee70341a8a57)

This second metal layer is thicker for carrying more current.Finally, we deposit a passivation layer using SiO₂ or Si₃N₄ to protect the chip.

![image](https://github.com/user-attachments/assets/96720b9c-1376-4584-b625-bebc24733177)

![image](https://github.com/user-attachments/assets/28051df2-427f-4a7a-b15c-c9e088f24cf7)








#Sky130 Day 4 - Pre-layout timing analysis and importance of good clock tree
##Timing modelling using delay tables
## Introduction to delay tables

![image](https://github.com/user-attachments/assets/2c20c7fa-6ef7-49f6-bfb5-e52ef8dc047f)



Power Aware Clock Tree Synthesis (CTS) involves techniques like clock gating to reduce power consumption by controlling the propagation of the clock signal. One common method is using logic gates such as AND or OR gates in place of buffers. For instance, in an AND gate, if the enable pin is set to logic '1', the clock signal will propagate through. But if it is set to logic '0', the clock gets blocked. In the case of an OR gate, the clock propagates when the enable is at logic '0', and it blocks the clock when the enable is at logic '1'. This ability to control the clock signal flow allows for power saving during idle or unnecessary operations.

![image](https://github.com/user-attachments/assets/0f4f4f96-4082-45c8-a13b-7ece8fc12b99)


Consider a scenario where a buffer in a clock tree is driving two other buffers. Normally, this would be a continuous path consuming power. However, using clock gating, we can replace that buffer with an AND gate, effectively controlling whether the clock should continue depending on the enable signal. While the rest of the circuit characteristics mostly remain the same, some aspects might change due to how the logic gate functions differently compared to a buffer. These changes will be analyzed in detail in subsequent steps.


![image](https://github.com/user-attachments/assets/85b7eaee-4150-4882-b3d8-0e41c0ec2c52)


Before performing this replacement (buffer with logic gate), certain assumptions are made about the circuit for simplification. These include assuming equal capacitance at various points in the circuit:

Capacitance at nodes C1, C2, C3, and C4 is assumed to be 25 fF each.

Capacitance of buffers BUF1 and BUF2 is taken as 30 fF each.

Therefore, the total capacitance at node A is 60 fF, and at nodes B and C, it is 50 fF each.


Some important observations from this structure are: the clock tree has two levels of buffering; each buffer at a level is driving the same load; and identical buffers are used at each level. However, despite these similarities, the output capacitance of the buffers across the circuit is not constant. This results in different output loads, which means the input signal transition times also vary. Consequently, this variation causes differences in propagation delays across the circuit.

To accurately capture and represent these delays, delay tables are used. These tables are generated by taking a single buffer from the circuit and testing it separately under controlled conditions. The input transition time is varied across a range—for example, from 10 picoseconds to 100 picoseconds—while simultaneously varying the output load. This helps in characterizing the delay behavior of the buffer under different scenarios. The collected data is then organized into a delay table, which helps in more accurate modeling during synthesis and timing analysis.



