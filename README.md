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
