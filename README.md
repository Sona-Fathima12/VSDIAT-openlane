# Digital VLSI SoC Design and Planning
# VSDIAT Openlane Sky130 Workshop
# Sky130 Day1- Inception of open-source EDA, OpenLANE and Sky130 PDK  
     
## How to talk to computers
## 0- Introduction to QFN-48 Package, chip, pads, core, die and IPs
![WhatsApp Image 2025-06-12 at 8 38 49 PM](https://github.com/user-attachments/assets/f9946eff-3473-4318-a6d5-6e2e4049589b)


Arduino Board-it is the image of an arduino board ,the yellow circle in it shows the chip,which controls the  board. This chip is designe using a process called RTL to GDSII flow. Arduino included both the hardware (the board) and software (the Arduino IDE) used to write and upload programs to the board.

![WhatsApp Image 2025-06-12 at 8 56 05 PM](https://github.com/user-attachments/assets/64b1bd30-eae2-40ae-8d31-5cf3598b58a3)


This diagram represnt a block level architecture of a Processor or SoC (System on Chip) and its interfacing component, focusing on the pinout and peripheral connections.This is a typical SoC interfacing diagram showing how various communication interface (I2C, UART, QSPI), memory (SDRAM, Flash, EEPROM), and power lines are connected around the Processor/SoC. It's useful in embedded system design for understanding pin usage and functional blocks.
![WhatsApp Image 2025-06-12 at 8 38 49 PM (1)](https://github.com/user-attachments/assets/46121903-7a16-41bf-b19c-7f9be63cb643)
![WhatsApp Image 2025-06-12 at 8 38 49 PM (2)](https://github.com/user-attachments/assets/2678b7b9-ccbb-4246-8572-998878c73bb2)
![WhatsApp Image 2025-06-12 at 8 38 51 PM (1)](https://github.com/user-attachments/assets/ca8959ca-e572-4ba3-9c70-735aa49de9b6)



components of chip
1)pads :it can send the signals inside the chip and vice versa

2)core :place where digital logic gates are placed in

3)die :size of the entire chip manufactured on silicon paper

![WhatsApp Image 2025-06-12 at 8 38 51 PM (3)](https://github.com/user-attachments/assets/081eba33-fe35-4c61-856d-fe5332e73256)


This image shows the top level layout of a System on Chip (SoC) design based on the RISCV architecture, which includes a variety of blocks used in integrated circuit (IC) design. This layout helps VLSI designer understand how the digital logic, analog IP and IO interfaces are arranged on the chip. It is part of the physical design or floorplanning process in chip design.
A typical chip consist of RISCV SoC,SRAM,dac,adc0,adc1,PLL,SPI,gpiobank; in that SRAM,dac,adc,PLL are Foundry IP's and the rest are Macros.
Foundry IPs and macros are pre-designed, verified blocks provided by semiconductor foundries (like TSMC or GlobalFoundries) that include essential components such as memory, IO cell, PLL, and standard cell, used to speed up and standardize chip design.

A **Foundry** in chip design refers to a company that manufactures semiconductor chips  based on designs provided by other companies.
Examples: TSMC, Samsung Foundry, GlobalFoundries.
These foundries do not design chips—they only fabricate them.

**IP** stands for **Intellectual Property.**
It refers to pre-designed, reusable blocks of logic or functions, like processors, memory controllers, USB interfaces, etc., that can be integrated into a chip to save time and effort during development.

**Macros** are large, pre-designed blocks such as memory units (like SRAM), analog block, or IO block, which are placed as fixed (hard) components during physical layout.

##   Introduction to RISC-V

RISC-V is an open-source instruction set architecture (ISA) developed at the University of California, Berkeley. The “V” stands for the fifth generation of RISC designs. Unlike other ISAs, RISC-V is free to use and doesn't require license fees. Many companies now support RISCV, and it works with popular operating systems and software tools.

RISC-V instructions are mainly 32 bit in size, but it also supports longer instructions for advanced features. It has versions for 32bit, 64 bit, and even 128 bit address spaces, though the 128 bit version is still experimental. In hardware, the chip is connected to its package using bond wires.

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
 

 This image shows how a stopwatch application works from high-level code to hardware execution. C program (shown in the center) is written to implement stopwatch functionallity, which is then compiled by system software (like Windows or Linux) into machine instructions. These are further translated into RISCV assembly code, which the hardware (chip layout) can understand and execute, producing the final stopwatch output.

 ![WhatsApp Image 2025-06-13 at 10 35 35 PM (1)](https://github.com/user-attachments/assets/c97254ab-d9ce-4f7f-9bcb-04c162b1844e)


This image explains how a high-level instruction like add x6, x10, x6 is processed down to the hardware level. The assembler converts this instruction into binary machine code based on the computer instruction set architecture (ISA). This binary is understood by the Register Transfer Level (RTL) design, which is then synthesized into a netlist. Finally, the netlist undergoes physical design to generate the chip layout that is implemented as real hardware capable of executing such instructions.
 

## SoC design and openlane
## 3-Introduction to all components of openlane digital ASIC design

![WhatsApp Image 2025-06-13 at 10 59 12 PM](https://github.com/user-attachments/assets/c32247df-4ecf-420d-969a-efa316c326e2)

This image provides an overview of the Open Source Digital ASIC Design flow using tools and data from open communities. At the center is ASIC (Application Specific Integrated Circuit), which is designed using the combination of EDA tools,RTL designs, PDK data.

**1) EDA tools**: (Electronic Design Automation), such as QFlow, OpenROAD, and OpenLane.it is used to design and verify PCB and IC.

**2) RTL designs**: (Register Transfer Level), sourced from platforms like librecores.org, opencores.org, and GitHub.

**3) PDK data**:PDK = Process Design Kit
 It is a Collection of files used to model a fabrication process for the EDA tools used to design an IC
  > Process Design Rules: DRC, LVS, PEX
  > Device Models
  > Digital Standard Cell Libraries
  > I/O Libraries
  PDK Data (Process Design Kits), such as the FOSS 130nm Production PDK developed by SkyWater and Google.

![WhatsApp Image 2025-06-13 at 11 13 32 PM](https://github.com/user-attachments/assets/9374210d-e3c3-4ace-86ba-ff9fb58e7c60)


Intel Pentium 4 Extreme Edition (P4EE) achieved 3.46 GHz clock speed using the 130nm process back in Q4 2004, proving that high speeds are possible at this node.
The Oklahoma State University  team achieved 327 MHz post-layout clock frequency for a single-cycle RV32i RISC-V CPU using a 130nm process.
A pipelined version could exceed 1 GHz, further demonstrating the node’s capability.


## Simplified RTL2GDS flow

![WhatsApp Image 2025-06-13 at 11 19 23 PM](https://github.com/user-attachments/assets/177ae6d6-530f-4100-9537-57e9bba520f0)

![WhatsApp Image 2025-06-13 at 11 55 06 PM](https://github.com/user-attachments/assets/5af98f48-3acc-43e6-8c67-06a09281c3e8)


It shows a simplified RTL  Transfer to GDSII (Graphic Data System II) flow, which is a standard process in digital chip design. The flow starts from the RTL description of a circuit and ends with the final layout file used for manufacturing. The steps include: Synthesis (converting RTL to a gatelevel netlist), Floorplanning and Power Planning (FP+PP) (defining block placement and power structure), Placement (arranging cells on the chip), Clock Tree Synthesis (CTS) (designing the clock signal distribution network), Routing (connecting all elements with metal wires), and Sign Off (final checks for timing, power, and design rules). The PDK (Process Design Kit) provides technology-specific information used throughout these steps. This flow is crucial for transforming high-level designs into manufacturable silicon chips.
In detail:
**Step 1: Synthesis**: it converts RTL to a circuit out of compoents from the standard cell library(SCL)

**SCL**:standard cell library: Standard cells have regular layout ,each has different views or models; 
> electrical,HDL,SPICE
> Layout(abstract and detailed)

![WhatsApp Image 2025-06-14 at 12 17 09 AM](https://github.com/user-attachments/assets/f7d0c01e-a423-4353-a2b3-ab0e688679ea)


**Step 2: Floor/Power planning** : The main objective of floorplanning or power planning in the RTL to GDSII flow is to organize and allocate space efficiently on the chip for various functional blocks, while ensuring proper power distribution and connectivity.

**chip foor planning**: partition the die between different system building blocks and place the I/O pads.

![WhatsApp Image 2025-06-14 at 12 17 11 AM](https://github.com/user-attachments/assets/31beb50b-f227-4528-9383-4d9d7c91c66b)


**Macro floor planning**: it is the process of placing large predesigned blocks (macros), such as memory or IP cores, on the chip layout in an optimal way to minimize area, improve performance, and ease routing congestion. 

![WhatsApp Image 2025-06-14 at 12 17 11 AM (1)](https://github.com/user-attachments/assets/32b9338a-552f-471d-8dba-4bd447e2aed9)


**Power planning**: it is the process of designing a power distribution network to ensure reliable and efficient delivery of power to all parts of the chip.

![WhatsApp Image 2025-06-14 at 12 07 06 AM](https://github.com/user-attachments/assets/312d4f70-a273-43ec-a80d-6fab3192a951)


**Step 3: Placement** :Place the cells on the floorplan row ,aligned with the sites.usually done in 2 steps:
    1.Global: to find positions for cells,cells may be overlapped
    2.Detailed: positions from global are minimally altered.

![WhatsApp Image 2025-06-14 at 12 17 10 AM](https://github.com/user-attachments/assets/02357cba-7048-40f8-afdf-f83436b4af90)


**Step 4: Clock Tree Synthesis** :it creates a clock distribution network,it helps to deliver the clock to all sequential elements(eg:FF) with minimum skew and in a good shape usually a tree(H,X....).
It  is the stage where the clock signal is distributed to all flip-flops in a balanced manner.The goal is to minimize clock skew and latency to ensure synchronous operationSpecial buffers and inverters are inserted to drive the clock signal across the chip.CTS helps meet timing constraints like setup and hold time.A well designed clock tree ensures reliable and predictable chip performance.


![WhatsApp Image 2025-06-14 at 12 17 10 AM (1)](https://github.com/user-attachments/assets/d5acace5-f28f-4fc6-9a59-be8143e0a676)


**Step 5: Routing** :implement the interconnect using the available metal layers.metal tracks form a routing grid and it is huge.it connects all the placed cells based on the netlist using metal layers .
It includes signal routing (connecting logic) and power routing (VDD and GND lines).Routing is done in two steps: global routing (path planing) and detailed routing (exact wire placement).Proper routing avoids congestion, crosstalk, and ensures timing closure.The final routed design is essential for generating the GDSII layout for fabrication.

![WhatsApp Image 2025-06-13 at 11 55 08 PM](https://github.com/user-attachments/assets/7fd57a7d-4340-49ff-bc97-ac63b1bc1e6c)



**Step 6: Sign off** :it is the final stage in the chip design flow where the design is thoroughly checked for correctness and readiness for fabrication.It includes critical checks like timing analysis, power analysis, signal integrity, DRC (Design Rule Check), and LVS (Layout vs Schematic).These checks ensure the design meets all functional, electrical, and physical requirement .


## Introduction to OpenLane and Strive chipsets

OpenLane is an open-source, automated flow that converts a digital design (written in RTL) into a physical chip layout (GDSII format) using a collection of tools like OpenROAD, Yosys, Magic, Netgen, and others. It is designed to run without human help in between steps  and its main goal is to create a "clean" GDSII — meaning the final layout has no errors in layout vs. schematic (LVS), no design rule check (DRC) violations, and no timing issues. OpenLANE supports the SkyWater 130nm open PDK and is used to create SoCs (System-on-Chips) through a fully open-source environment. The striVe family of SoCs was built using OpenLANE and includes different versions with various RAM configurations and design modules.

OpenLANE supports two operation modes: Autonomous, where everything runs automatically with a push of a button, and Interactive, where each design step is done manually for better control and learning. It includes 43 example designs, each with optimal settings, to help users understand and experiment with the design flow. The striVe SoC family includes variants like striVe 1, 2, 2a, 3, 5, and 6, each offering different memory setups and testing features. Overall, OpenLANE makes chip design more accessible, especially for students and reserchers, by offering a complete and open platform from RTL to GDSII.

## Introduction to OpenLane and detailed ASIC design FLOW

![WhatsApp Image 2025-06-14 at 1 42 15 PM](https://github.com/user-attachments/assets/20fee7e6-7022-4f11-b150-4aabfc7d5402)


OpenLANE includes a design exploration utility that is also used for regression testing. In this process, OpenLANE is run on around 70 designs to make sure everything is working correctly. The results are compared with the best-known previous resultss to confirm that recent changes have not caused any performance or quality issues.

Design for Test (DFT) is a step that ensures the chip can be tested after manufacturing. It includes several tasks such as scan insertion, automatic test pattern generation, pattern compaction, fault coverage measurement, and fault simulation. These help in detecting defects in the final silicon chip.

After DFT, physical implementation is done using the OpenROAD tools. The major steps include floor and power planning, adding decoupling capacitors and tap cells, global and detailed placement of components, post-placement optimization, clock tree synthesis (CTS), and global and detailed routing. These steps physically arrange and connect the circuit on the chip.

Since CTS and post placement optimization change the netlist, it is important to verify that the design's logic remains the same. This is done using the LCE tool in Yosys, which performs formal verification to ensure that the functional behavior has not changed due to netlist modifications.

![image](https://github.com/user-attachments/assets/89db5fe6-2621-446a-8bf1-ec3343e12c7b)
![image](https://github.com/user-attachments/assets/73630be3-8bc6-4ab6-94db-6112c8be4491)
![image](https://github.com/user-attachments/assets/d68dfe39-8c76-413c-ad85-776b1e12b384)


During chip fabrication, metal wires can act as antennas and collect charge, which may damage transistor gates. This is called an antenna rule violation. To fix it, we can either bridge the wire to a higher metal layer or add antenna diode cells to release the charge. OpenLANE uses a preventive method by placing fake antenna diode cells next to every cell input after placement. If the antenna checker detects a real violation, these fake diodes are replaced with actual diode cells.

Static Timing Analysis (STA) checks if the chip design meets timing requirements. This involves extracting resistance and capacitance information from the layout using DEF2SPEF, then running STA with the OpenSTA tool. Any timing violations are reported for correction.

Finally, physical verification is performed. Design Rule Checking (DRC) ensures the layout follows manufacturing rules, which is done using Magic. Layout Versus Schematic (LVS) checks that  physical layout matches the circuit logic. This is done using Magic and Netgen, and a SPICE netlist is also extracted from the  layout for further analysis.


## Get familiar to open-source EDA tools
## OpenLANE directory structure in detail

cd : opens the particular folder

ls : lists the content of the folder

pwd : shows the present working directory

mkdir : to make a new directory

command --help : shows the complete use that command

clear : clears the terminal screen


# LAB DAY 1

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


# LAB DAY 2

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


after every logic gate and flip-flop from the netlist is assigne a proper shape and size, the next important step is placing these components onto the chip floorplan. The floorplan  already contains the defined input and  output ports, the netlist describing connectivity, and the physical dimensions of each component. With all this information, we now have a physical representation of each gate, which allows us to start positioning them on the floorplan based on how they are connected logically  .

During placement, it is important to ensure that the locations of preplaced cells remain unchanged. These preplaced blocks serve specific roles in the design and must not be moved or overlapped by other cells. Placement must be done carefully so that no cell is positioned over the existing preplaced cells, and all logic gates are placed in a way that maintains the required signal flow. This ensures that logical connections are preserved, timing constraints are met, and signal delays are kept minimal.

Initially, the placement is done in such a way that all gates are located close to their related input and output pins to support better performance. However, upon examining the layout, it is noticed that the distance between FF1 of Stage 4 and input Din4 is longer compared to other. This could potentially impact timing and delay . To address this, optimization of the placement is needed to reduce this distance, there by improving the overall timing and efficiency of the circuit layout.

step 3:Optimize placment.

It is the solution to the problem of distance in placement area. So we use repeated repeaters are basically buffers that will recondition your original  signal that will make a new signal which replicates the original signal and send it again .
As repeaters  increase area will be loss inside the core.The following pictures I attached are showing the repeaters used in the placement of each set of cells.

In the first set the distance between Din1 and FF 1 is less . The wirelength is less and therfore there is not that much resistance and we can directly connect them together and from ff1 to 1 same there is no any large wirelength so we can connect to the together and similarly 1 to 2 and 2 to FF 2 and ff 2 to Dout1 can be connected without any problem because it has  acceptable wire length and there is no any huge capacitance so they can connected.

![image](https://github.com/user-attachments/assets/a4e7759f-aab3-48e9-94cf-4417102eedcf)

In second set the distance for wirelength is huge. So the capacitance is very high. So we use 2 buffers called  repeaters.But in someparts there is no delay. That means from ff1  to ff2 there is no delay .and after that we can connect ff2 to Dout2

![image](https://github.com/user-attachments/assets/5cedc953-651a-45ca-bb45-fc1470d75cc3)

similar to stage 2, in Stage 3 also we required the buffer between gate2 and FF2.


![image](https://github.com/user-attachments/assets/3e93cc95-abbe-44ac-9cf1-e31f0fa11106)

In sEt 4, it is big tricky compared to the other three stages.So here the Din4 cant reach f f1 because of the pre placed cells so a buffer is set there so Din4 can reach the repeaters and then f f 1 and from ff1 to 1. and if we look 1 to 2, it cant be reached that easily because there is a huge distance. so a buffer is placed also we can see that the crisscross with the second set, so we can say that 4th set is in  metal 3 layer set 2 in metal 1 or 2 layer,3rd set in metal layer 4. so we have to check that what we have done is correct or not first. for that,. We need to do a timing analysis by considering the ideal clocks and according to the data of analysis. we will understand that a placement is correct or not.
![image](https://github.com/user-attachments/assets/6ac084d3-08ac-4da2-a4d3-f060706968d2)


## Need for libraries and  characterization
step 1: logic synthesis: arrangeent of gates that will represent your orginal functionality that you have described usinf RTL.
step 2: floorplanning: we import the output of logic synthesis that is netlist and decide the size of core and die(depends on the number of gates present in the netlist).
step 3: Placement: logic cells are placed in chip
step 4: clock tree synthesis(CTS) : that will take care of clock which reach every clock points.
step 5: routing : routing means connecting all the components together with metal wires so that signals (data, control, power) can move correctly between them.
step 6: static timing analysis : to analyse what is setup time ,old time,what is the maximum achieval frequency.

one thing common accross all stages are gates or cells



# LAB DAY 2 (BALANCE)

5.Load generated placement def in magic tool and explore the placement.

Commands used:
![Capture 18](https://github.com/user-attachments/assets/5bd9de61-a3bc-4456-a9b2-12853fbb6ce8)
![Capture 19](https://github.com/user-attachments/assets/269048ed-c8bf-4404-97b5-2e79d192b4d7)
![Capture 20](https://github.com/user-attachments/assets/df167c0a-1627-4dbc-afb7-aa9f1c87579b)

## Cell design and characterization flow.
## input for cell design flow

![image](https://github.com/user-attachments/assets/612d3dab-bb87-4cbc-b89e-8a9e987294d2)


In cell design flw, basic components like gates, flip-flops, and buffers are called standard cells, and they are stored in a library. each function, like an inverter, may have many versions with the same logic but different sizes or strengths  .
The inverter has to represented in form of the shape, drive strength, power charracteristic and so on. Here cell design flow is devided into three parts.

![image](https://github.com/user-attachments/assets/1d9fa6c8-3402-4543-8bb4-001c6e35c1ae)

1.Inputs :To design these cells, we need some important inputs like the PDK (Process Design Kit) which includes all the technology details, DRC and LVS rules which ensure the layout is correct and matches the circuit, SPICE models that describe how the transistors behave electrically, and user specifications like speed, area, and power. these inputs help us create a proper and working version of the cell to add to the library. 

2.Design steps : It has 3 steps **circuit design**(implement the functions and model NMOS and PMOS inorder to meet library requirements),**layout design**,**characterization**

3.Outputs :CDL(circuit design language,GDSll ,LEF




## Circuit design step

In the design process of a standard cell, the height of the cell is decided by the distance between the power rail (VDD) and ground rail (GND), while the width depends on the required timing and drive strength. The design process has three main steps: circuit design, layout design, and characterization. In circuit design, we first create the logic function (like an inverter), and then model it using PMOS and NMOS transistors to match the library standads. The outputs of this step include files like CDL, GDSII, LEF, and an extracted SPICE netlist. In the layout design step, we take the transistor-level circuit and draw its layout using PMOS and NMOS networks. 
![image](https://github.com/user-attachments/assets/24650768-b9ae-4d53-8015-e77fcc84e23c)


We then create network graphs, find an Euler’s path to optimize the layout, and draw a stick diagram based on it. This stick diagram is then turned into the actual layout following design rules. Once this layout is ready, we extract parasitic components like resistance and capacitance. The final step is characterization, where we simulate the cell to  measure its timing, power, and noise behavior. 

## Layout design step

![image](https://github.com/user-attachments/assets/c00d46d2-f8ab-4e1c-8746-388f5bdcf51c)
![image](https://github.com/user-attachments/assets/3a076c24-4c1a-4c8a-aa4b-3ec4cae905e8)
![image](https://github.com/user-attachments/assets/f14264e7-9139-40ad-b44c-7c92bca1e202)

In layout design, the first step is to built the logic function using PMOS and NMOS transistors. From this, we create PMOS and NMOS network graphs that show how the transistors are connected. Then, we find the Euler’s path, which is a way to arrange the transistors in a line to make the layout compact and efficient. using this path, we draw a stick diagram, which is a simple sketch showing how different parts will be placed. This stick diagram is then turned into the actual layout following design rules . the final layout will include details like cell width, height, pin positions, and other specifications. aftre the layout is complete, we extract parasitic elements (like small resistances and capacitances) and move to the characterization stage, where we measure the cell’s timing, power, and noise. Before that, the layout is saved in GDSII format, and the electrical version is saved as a SPICE netlist for simulation. 

## Typical characterization flow

In the characterization process,
![image](https://github.com/user-attachments/assets/a11861b9-0ab3-4ed0-82e7-3df7f7212537)
![image](https://github.com/user-attachments/assets/f196ca44-4c7f-415c-9bab-2544d7c2d151)

1. to load the transistor model
2. reading the extracted SPICE netlist.
3. identify the behavior of the cell, like if it’s an inverter or buffer.
4. read the subcircuits of inverter.
5. attach necessary power supplies
6. apply the input signal or stimulus.
7. necessary output capacitance should be provided.
8. add the correct simulation command—like .tran for transient simulation or .dc for DC simulation.

   ![image](https://github.com/user-attachments/assets/28bef949-6bdc-4d95-a350-9c03833af553)

All these steps are written into a configuration file and given to a tool called GUNA, which runs the simulations and gives us information about timing, power, and noise. 


## General timing characterization parameters

## Timing threshold definitions

When analyzing timing in digital circuits, we use something called timing threshold definitions to understand key points on a waveform. For example, when a signal is rising or falling, we don't measure the entire transition  instead, we look at certain percentage points. For slew rate (how fast a signal changes), we define points like Slew_low_rise_thr and Slew_low_fall_thr, which are usually around 20 to 30% of the voltage swing and Slew_high_rise_thr and Slew_high_fall_thr, which are around 70 to80%. These points help calculate how quickly a signal rises or falls.

![image](https://github.com/user-attachments/assets/fa86e5bc-c918-443d-bd61-50ed8c16131a)
![image](https://github.com/user-attachments/assets/aa7be48d-0fa7-494c-9bd7-e7347028a3d6)
![image](https://github.com/user-attachments/assets/fc19c7f2-fef2-4cef-b9ae-02e1d69f6be5)
![image](https://github.com/user-attachments/assets/bda25642-dcb5-40ef-a1b9-f1841b79b8df)


Similarly, to measure delay, we look at when the input or output waveform crosses 50% of the voltage level  these are called in_rise_thr, in_fall_thr, out_rise_thr, and out_fall_thr. These timing points are important for accurate delay and performance calculations in digital cell design.

![image](https://github.com/user-attachments/assets/f6ba0e88-c43b-4529-b633-5b818d28d6c9)
![image](https://github.com/user-attachments/assets/38c7d552-da95-41b2-8141-35434ae77f59)


## Propagation delay and transition time

![image](https://github.com/user-attachments/assets/6feae831-5482-45e0-907f-a1a1358cb932)

To calculate the delay in a circuit, we subtract the time when the input signal reaches its threshold (typically 50%) from the time when the output signal reaches its threshold. So, delay = time(out_thr) - time(in_thr).

![image](https://github.com/user-attachments/assets/760f044e-37f7-41ec-ab7a-b70fe49538af)

If the thresholds are chosen incorrectly—like placing them too close to the top or bottom of the waveform—it can result in a negative delay, meaning the output changes before the input, which is physically incorrect and not acceptable.

![image](https://github.com/user-attachments/assets/8985406f-8e80-4372-a6dd-b17def432477)

Even with the correct threshold value, negative delay can still happen if the waveforms overlap in the wrong way, showing why threshold choice and waveform behavior both matter.

![image](https://github.com/user-attachments/assets/e11e3ef6-d1a6-43ec-a7f1-829330e6c572)


Similarly, transition time (how quickly a signal changes) is calculated by subtracting the low threshold time (e.g., 20%) from the high threshold time (e.g., 80%).

a. For a rising edge,Eqn:  slew_high_rise_thr - slew_low_rise_thr 

b. for a falling edge, Eqn:  slew_high_fall_thr - slew_low_fall_thr.

These calculations help us understand the speed and performance of a digital circuit. 

![image](https://github.com/user-attachments/assets/8769604d-9b00-43a3-8a28-f934fc31a4ca)



# Sky130 Day 3 - Design library cell using Magic Layout and ngspice characterization

## Labs for CMOS inverter ngspice simulations 
## IO placer revision

we have completed floorplanning and placement for our chip layout. But if we want to revise the floorplan—especially how the IO pins are arranged—we can do that too. For example, in the default setup, the pins are placed at equal distances around the chip. But if we want to change their positions, such as moving them to specific sides, we can adjust the configuration settings using the set command. To enable custom pin placement, we first check the available configuration switches and change the setting env(FP_IO_MODE) from 1 to 2. After that, we re-run the floorplanning step to reflect the updated pin layout. Once the new floorplan is generated, we can check the changes using Magic by opening the layout with the magic -T command. 


, we can see that all the IO pins have shifted to the lower half of the core, leaving the upper half empty. This confirms that our custom pin placement settings have taken effect, allowing us to tailor the design based on routing ease or other layout considerations.

## SPICE deck creation for CMOS inverter

In VTC (Voltage Transfer Characteristic) SPICE simulations, the first step is to create a SPICE deck. This is essentially a netlist that contains all the connectivity details of the components used in the circuit. It includes the inputs provided to the circuit and the output points where simulation results are observed. One important part is defining how each component is connected, especially the substrate pins, which help tune the threshold voltage of the PMOS and NMOS transistors. We also specify the values for PMOS and NMOS—here, both transistors are taken with the same size for simplicity. 

![image](https://github.com/user-attachments/assets/a885cd55-a7e6-46d1-86ed-f6b0e409f6fa)
![image](https://github.com/user-attachments/assets/7e343282-b87e-4f22-a449-a025926a761e)


Next, we identify and label the nodes in the circuit, which are the points between connected components. These nodes are then named meaningfully—for example, Vin for the input node, Vss for ground, Vdd for power, and out for the output. Once the nodes are named, we can write the SPICE deck in the proper format. The transistor connections are listed as: Drain, Gate, Source, and Substrate. For the PMOS (M1), the drain is connected to the output, gate to the input, and both source and substrate to Vdd. For the NMOS (M2), the drain is also connected to the output, gate to input, and both source and substrate are connected to ground (0). 

![image](https://github.com/user-attachments/assets/498ce820-9c95-4633-98d5-5029cb6e292e)

## SPICE simulation lab for CMOS inverter

![image](https://github.com/user-attachments/assets/b6fc1047-ac9d-484e-91d5-5e2aab2b0d2f)

 we have defined the connectivity of the CMOS inverter. Now, we add connections for other essential components such as the load capacitor and power sources. The load capacitor is connected between the output node (out) and ground (node 0), with a value of 10 femtofarads (10fF). The supply voltage, Vdd, is applied between the Vdd node and ground with a value of 2.5V. Similarly, an input voltage source is connected between the Vin node and ground, also set at 2.5V. To observe how the output responds to different input values, we set up a simulation command that sweeps Vin from 0 to 2.5 volts in small steps of 0.05V. 

For the simulation to work correctly, we also include model files, which describe the behavior of the NMOS and PMOS transistors in detail. After setting everything up, we run the SPICE simulation and observe the output graph.

![image](https://github.com/user-attachments/assets/378c8626-737e-4601-ba8a-67db55361b6f)

In this case, both NMOS and PMOS have the same width, and the resulting transfer characteristic curve is shifted left from the center.

![image](https://github.com/user-attachments/assets/69fb2966-e7d0-4866-8c47-a1a5c988947b)
![image](https://github.com/user-attachments/assets/a2f59624-22e8-4b2b-9032-61df8cb64b04)
![image](https://github.com/user-attachments/assets/4a30d698-62e2-4be6-9b70-7b9a751faef3)

 In this simulation above, we increase the PMOS width to 2.5 times that of the NMOS. This change results in a more balanced graph, where the transfer characteristic lies exactly in the middle. This demonstrates how the sizing of transistors directly affects the switching point and performance of the inverter. 
 
## Switching Threshold Vm

Both CMOS models, whether they have equal or different transistor width , serve different purposes and have their own applications. when we compare their output waveforms, we observe that the overall shape remains the same regardless of voltage level , which shows the robustness of CMOS technology
![image](https://github.com/user-attachments/assets/f9300be7-1b32-4fde-9484-7cc45814fcb4)

As Vin increases from low to high, the output Vout switches from high to low, maintaining the core inverter behavior. This consistency, even when the NMOS and PMOS sizes are varied, is why CMOS logic is so commonly used in digital gate design it remains stable, efficient, and reliable. 
![image](https://github.com/user-attachments/assets/8e807945-6fba-4c60-95d6-36d38346a59b)

One key parameter that reflects the robustness of a CMOS inverter is the switching threshold, Vm. This is the point where the input voltage equals the output voltage (Vin = Vout). 

![image](https://github.com/user-attachments/assets/f8fe14dd-26ab-4910-ac7e-27cc7234fca0)

In the graph shown, this occurs around 0.9V. At this point, both the NMOS and PMOS transistors may be partially on, which can cause a direct current path from Vdd to ground, leading to leakage current. This critical point helps in analyzing th the performance and power consumption of CMOS circuits. by  comparing the graphs, we also gain insights into the operating regions of PMOS and NMOS, and understand how current flows differently in each type of transistor depending on the input voltage.

## Static and dynamic simulation of CMOS inverter

In dynamic simulation of a CMOS inverter, we focus on understanding the rise and fall delay how quickly the output changes from low to high (rise) and from high to low (fall) in response to a changing input. Unlike the previous simulations that used a DC sweep, this one uses a pulse input signal.  everything else in the setup, including the circuit and component values, remains the same.  simulation command used here is .tran, which stands for transient analysis, allowing us to observe how voltages change over time. 
![image](https://github.com/user-attachments/assets/a3bf05cd-2cd2-41a4-9b56-770d4a9a4ad2)
![image](https://github.com/user-attachments/assets/f73087ee-26ee-4e43-a19d-76bd1517fb46)

From the output, we get a Time vs Voltage graph. By examining this graph, we can measure how long it takes for the output to respond when the input pulse transitions. The rise delay refers to the time taken for the output to go from low to high, while the fall delay is the time taken to drop from high to low. These delays are influenced by factors like the switching threshold (Vm), transistor sizes, and load capacitance. Analyzing them helps us understand the speed performance of the CMOS inverter in real operating conditions. 





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



# LAB DAY 3
## Lab introduction to Sky130 basic layers and lef using inverter
### COMMANDS:

![Capture 21](https://github.com/user-attachments/assets/15048b0a-9dea-4966-9ab1-9876b0da422c)
![Capture 22](https://github.com/user-attachments/assets/a1113f37-ac21-4f33-b136-220cceae1f8f)

### THE LAYOUT:
![Capture 23 1](https://github.com/user-attachments/assets/49c11e99-36b3-4f00-8e2b-3efff0e95a1d)

### NMOS identified
![Capture 24](https://github.com/user-attachments/assets/b135322f-83d3-49d8-b334-bf222b344e89)
### PMOS identified
![Capture 25](https://github.com/user-attachments/assets/6ede103d-3a14-4277-85ad-1ca26e37338b)
### Y connectivity to PMOS and NMOS drain verified
![ect](https://github.com/user-attachments/assets/d7379ac5-9083-4d13-ac2a-260ac53458e7)

### PMOS source connectivity verified.
![Capture 27](https://github.com/user-attachments/assets/27cd166b-08a5-49be-998d-872ca9f1abdc)
### NMOS source connectivity to VSS veified
![Capture 28](https://github.com/user-attachments/assets/454275e1-e38a-4c26-a2dc-9c3e12d5ce33)
### DRC error
![Capture 29](https://github.com/user-attachments/assets/88707405-d079-4d8b-8113-61b072814fbe)
![Capture 30](https://github.com/user-attachments/assets/2236b3f0-a652-4199-bc72-27f3e620a0c2)
### after giving extraction commands:
![Capture 31](https://github.com/user-attachments/assets/5fb6af4a-59ea-44c7-b859-435bf5b8d602)
![Capture 33](https://github.com/user-attachments/assets/3fc34310-77c4-4ce4-b969-50e623bd6a3b)
### Measuring unit diatance in the layout after grind on in the windows:
![Capture 34](https://github.com/user-attachments/assets/c43e244f-7da5-4f34-a2b6-999d5aed60bb)

### commands for ngspice simulation
![14 PIC](https://github.com/user-attachments/assets/e5d07f88-3070-405b-a53b-08d2c09e7645)

### spice file for ngspice simulation
![15N PIC](https://github.com/user-attachments/assets/0647968e-0fe7-4314-805a-dadd726dfa6a)
![16N PIC](https://github.com/user-attachments/assets/825856aa-2de4-42a9-8a6f-0fe13744f14d)

output:
![17 PIC](https://github.com/user-attachments/assets/75d4a43b-95b6-4ab1-8b0c-345bc90a89cb)

### if we change C3 value to 0.2fF
![18 PIC](https://github.com/user-attachments/assets/e8b1f79c-013a-4bc3-8310-ccbbf1845647)
![19 PIC](https://github.com/user-attachments/assets/5ce7e494-ea53-4842-8a82-77f54ad0a2f1)

WE GET AN EVEN MORE SMOOTHER GRAPH

![20 PIC](https://github.com/user-attachments/assets/04e4992f-0465-495a-a53c-297931d9a2e6)

### Rise transition time calculations

![WhatsApp Image 2025-06-18 at 10 13 29 PM](https://github.com/user-attachments/assets/de645b5b-ce4e-4df5-8131-5f83ca6ed967)

Rise Transition Time Calculation 

Rise Transition Time = Time taken for output to rise to 80% - Time taken for output to rise to rise to 20% 

20 % of output = 660mV 

80% of output = 2.64V 

Rise transition Time = 2.24638 – 2.18242 = 0,06396 ns = 63.96 ps 

![WhatsApp Image 2025-06-18 at 10 13 53 PM](https://github.com/user-attachments/assets/39e866f0-02f6-4e11-b16a-5c8451af672c)


Fall Transition Time Calculation  

Fall Transition Time = Time taken for output to fall to 20% - Time taken for output to fall to 80% 

20 % of output = 660mV 

80% of output = 2.64V 

Fall Transition Time = 4.0955 – 4.0536 = 0.0419 ns = 41.9 ps 


![WhatsApp Image 2025-06-18 at 10 14 22 PM](https://github.com/user-attachments/assets/c0a29994-cf06-408d-ad67-d0d335f4a639)


Rise Cell Delay Calculation 

Rise Cell Delay = Time taken for output to rise to 50 % - Time taken for input to fall to 50% 

50 % of 3.3 V = 1.65 V 

Rise Cell Delay = 2.2144 – 2.15008 = 0.06136 ns = 61.36 ps

![WhatsApp Image 2025-06-18 at 10 14 54 PM](https://github.com/user-attachments/assets/d933c87d-21e0-4625-8a6d-36b960c20f09)

Fall Cell Delay Calculation  

Fall Cell Delay = Time Taken For Output to Fall to 50% - Time taken for input to rise to 50 % 

50 % of 3.3V = 1.65 V 

Fall Cell Delay = 4.07 – 4.05 = 0.02 ns = 20 ps 


### Lab introduction to Sky130 pdk's and steps to download labs
To know more about the Magic DRC we can go to the website:-  http://opencircuitdesign.com/magic/Technologyfiles/TheMagicTechnologyFileManual/DrcSection

Link to Google_Skywaters Design Rules: -  https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

For reference , we can use the github repo of Google-Skywater: -  https://github.com/google/skywater-pdk


### Commands 
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

1.To extract the lab files from the downloaded file:tar xfz drc_tests.tgz

2.Go into the lab folder:cd drc_tests

3.See all files and folders (even hidden ones):ls -al

4.Open the .magicrc file:gvim .magicrc

![21 PIC](https://github.com/user-attachments/assets/ba4542e3-a57b-4d7e-bdf8-31c0ad59438e)
###Content of .magicrc file: vi .magicrc
![22 PIC](https://github.com/user-attachments/assets/f3dd88d7-8e7a-4e6a-b49b-fc9742186d13)

![23 PIC](https://github.com/user-attachments/assets/6791b1cd-4338-451e-be35-bc38a97fdff8)
### Lab introduction to Magic and steps to load Sky130 tech-rules
command: magic -d XR
![24 PIC](https://github.com/user-attachments/assets/5f86a98c-727c-47fa-9fd8-5b8b6cd76b37)

### select the any layout area and check drc why

![26 PIC](https://github.com/user-attachments/assets/3ec75290-9498-4314-8a2a-158716302eb4)

then click on a blank area in Magic.and move the mouse over the metal3 contact icon.and press p on the keyboard.then type **paint pek** in tkon window then type **cif see VIA2**
you can see black squares (VIA2) appear in the layout.

![26Q PIC](https://github.com/user-attachments/assets/08b2b6fd-46cf-4482-942b-09c1e76e2283)
### Lab exercise to fix poly.9 error in Sky130 tech-file
### open the poly.mag file:load poly.mag

![27 PIC](https://github.com/user-attachments/assets/c65f8dd8-747d-4330-a734-1bc46e6eede6)

![28 PIC](https://github.com/user-attachments/assets/dd740c2c-b2ee-425a-a009-649a17c29cea)
![29 PIC](https://github.com/user-attachments/assets/bc1d1e47-ab0c-43d5-8a47-d51772e4b68a)

To find the error  look at the sky130A.tech file which is present in the drc_tests directory.
and added changes in it
![32 pic](https://github.com/user-attachments/assets/437590c6-1210-4a2c-b523-4f3104f412aa)
![33 pic](https://github.com/user-attachments/assets/66afa47e-2102-4e62-94e5-f8c9d992fa3b)

the command tech load sky130A.tech in the tkcon terminal.then drc check

![34 pic](https://github.com/user-attachments/assets/2fa04d21-1f8a-4e00-bba2-c9f0e3b38185)
### Lab exercise to implement poly resistor spacing to diff and tap
for correctly implement poly resistor spacing : add few more changes and save
![35 pic](https://github.com/user-attachments/assets/8fbeb590-be36-4b70-a4c4-60f542fffba6)
![36 pic](https://github.com/user-attachments/assets/179ed38f-ad84-42df-b386-8ccafeedea73)
![37 pic](https://github.com/user-attachments/assets/ce844794-ff15-4a22-90dd-2f84ce47506b)

### Lab challenge exercise to describe DRC error as geometrical construct
then we will make some changes in sky130A.tech file which are as follow


![38pic](https://github.com/user-attachments/assets/df01b630-c200-451e-9cf9-cfa3eddc590a)
![39pic](https://github.com/user-attachments/assets/96bb609d-448e-4185-9164-7345d2be7813)

To find the nwell.6 model error, open the nwell.mag file in the magic tool. In the figure, the deep nwell is shown in yellow stripes and the nwell is shown in dotted green  pattern.
![40 pic](https://github.com/user-attachments/assets/7abac196-4935-4049-b20e-b68640fb65c3)

the error is:
![41pic](https://github.com/user-attachments/assets/7683057d-4c64-494c-a50a-7020666ffb1f)

### Lab challenge to find missing or incorrect rules and fix them
then we will open the magic tool and execute the commands drc style drc(full) and drc check.
![42pic](https://github.com/user-attachments/assets/324d096b-2ab7-4af9-b14e-a46371e12873)








# Sky130 Day 4 - Pre-layout timing analysis and importance of good clock tree
## Timing modelling using delay tables
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



## Delay Table Usage – Part 1:

![Screenshot (48)](https://github.com/user-attachments/assets/a5d6cbb2-11de-4ccc-8030-1af15895fbf7)

In Power Aware Clock Tree Synthesis (CTS), delay tables are used to estimate the delay introduced by buffers based on input transition time (slew) and output load capacitance. For example, in the given figure, if the input transition to buffer CBUF1 is 40ps and it drives a 60fF load, the corresponding delay falls between entries x9 and x10 in the CBUF1 delay table. Since this exact load isn't listed, the delay is interpolated and represented as x9′, which helps designers estimate the delay more accurately for intermediate values. This process ensures more precise clock timing calculations during CTS. The same principle applies for buffer CBUF2, where the input transition is assumed to be around 60ps, and the output load is 50fF. Looking at the delay table for CBUF2, the corresponding delay is y15.


## Delay Table Usage – Part 2:

By combining both delays, the total delay from the input to each clock sink (output point) is calculated as x9′ + y15, while ignoring wire delays for simplicity. Since the buffer structure is symmetric and the output loads at all clock endpoints are equal, the skew (difference in arrival times of the clock signal) is zero. However, if the load at each endpoint (B and C) were different, the delay would vary due to different output loads, leading to non-zero skew. These tables, therefore, not only help in estimating individual buffer delays but also play a critical role in balancing clock paths, reducing skew, and enabling power-efficient and reliable CTS.


## Setup Timing Analysis and Introduction to Flip-Flop Setup Time

![image](https://github.com/user-attachments/assets/887b0632-6b4c-460e-b0dc-3f72636e7547)


an ideal clock – that means a perfectly regular clock signal. Suppose the clock frequency is 1 GHz, so the clock period is 1 ns.

Imagine we have two flip-flops.One is the launch flip-flop, which sends out data at time = 0 ns.The second is the capture flip-flop, which receives data at time = 1 ns (after one full clock cycle).Between these two flip-flops, there is combinational logic – like gates and circuits that process the data. The time taken by this logic to process the data is called θ (theta).Now, for proper working, this logic delay must be less than the time between two clock pulses. So initially, we say:θ < T (means θ should be less than 1 ns).But here’s the catch – the capture flip-flop also takes some time to properly store the data. This is called the setup time (S). It is the time required before the clock edge for the input data (D) to settle down so it can be reliably captured and shown at the output (Q).

![image](https://github.com/user-attachments/assets/a5963720-0a91-42cd-8c26-7811b3d6c90a)

Inside the flip-flop, elements like MUX1, MUX2, and other transistors introduce delay, which is why this setup time comes into play.So now, we must leave some time for this setup as well. That changes our equation to:θ < T - S.For example, if setup time S = 0.01 ns, then θ should be less than 0.99 ns for proper operation.

![image](https://github.com/user-attachments/assets/b1de9bbf-7ac3-43f7-8edc-7c3cfe348683)

## Introduction to Clock Jitter and Uncertainty

![image](https://github.com/user-attachments/assets/383ef438-077e-46cb-9a15-95cf0f4f6c04)


In the real world, the clock is not always perfect. It's usually generated by a PLL (Phase-Locked Loop). The clock signal should arrive exactly at 0 ns, 1 ns, 2 ns, etc., but it has got some positive and negative variations.that clock source might or might not generate a clock period which provides exactly at T ns.This small timing variation in the clock signal is called jitter. It is a temporary shift from the expected clock time and can affect how correctly the data is captured.

Also, there is another factor called clock uncertainty , which accounts for such timing variations in the clock network. It acts like a safety buffer in design.

![image](https://github.com/user-attachments/assets/53ee7c0f-c138-467b-a1e1-f86d8c579ee3)

So now, along with setup time, we also need to consider this uncertainty. That further modifies our timing condition:θ < T - S - US

Suppose:
a. Setup time S = 0.01 ns .Clock uncertainty  = 0.09 ns

Then the equation becomes:
θ < 1 - 0.01 - 0.09 = 0.9 ns

So, the total logic delay (θ) must be less than 0.9 ns for the circuit to function correctly.

This final timing check is what we use in real-world STA (Static Timing Analysis) to make sure data moves from one flip-flop to the next without any setup violations.
![image](https://github.com/user-attachments/assets/054296db-1f5c-4b37-b47c-6886d46eae22)
![image](https://github.com/user-attachments/assets/ddce4f28-dd92-435d-9c2d-80ee2b6234c1)
![image](https://github.com/user-attachments/assets/a95a2a38-fc73-4f4c-90c7-c7bb93e8bdf0)



## Crosstalk and clock net shielding 

![image](https://github.com/user-attachments/assets/63363c2d-1d4c-4c08-8877-2777a5fb77d0)

Clock net shielding is a technique used in chip design to protect the clock signal from external interference. Normally, we build the clock tree so that the delay (or skew) between the launch and capture flip-flops is zero, meaning both receive the clock at the same time. 
![image](https://github.com/user-attachments/assets/03a07346-34a0-4115-8f2c-baa2ea2bf80e)

if the clock net is left unprotected, it can be affected by nearby signal wires due to something called coupling capacitance. When these nearby wires (called aggressors) switch states, they can create noise or glitches on the clock net (the victim), causing delays—especially when switching from logic '1' to '0'. This is known as delta delay and it disturbs the perfect synchronization of the clock, making the skew non-zero. To prevent this, we use shielding, where grounded or powered wires are placed between signal wires to block this interference. These shielding wires don’t switch, which helps break the coupling path and protect the clock net from glitches and delay. 

We saw tht the amount of delta delay because of the bump when we are switching from logic '1' to logic '0'. And skew is not anymore 0 here. So the impact of crosstalk delta delay is that it make the skew value non-zero.
![image](https://github.com/user-attachments/assets/756e3ccc-83da-42ce-bfe5-c01e051ebc66)


## Timing analysis with real clock using openSTA 

## Setup timing analysis using real clocks 

In real-world circuits, the clock signal doesn't reach flip-flops instantly like in an ideal case because it travels through buffers and wires, which introduce delay. So, the clock reaches the launch and capture flip-flops at different times due to these elements. This changes our timing analysis. Originally, we used a simple condition like θ < T, but now we have to account for delays.
![image](https://github.com/user-attachments/assets/3c0d6bfe-85d5-4a40-afdd-c5cc352db28c)

We call the delay on the launch side  as ∆1, and on the capture side  as ∆2. The difference between them (∆1 - ∆2) is known as skew. Also, we must include factors like propagation skew (s) and clock uncertainty . So, the setup timing equation becomes (θ + ∆1) < (T + ∆2 - s - US)
![image](https://github.com/user-attachments/assets/58e24856-c3a5-4844-a046-90f48adbca02)

where the left side is the data arival time and the right side is the data required time. If required time minus arrival time is positive, the setup is valid and if it's negative, we call it a negative slack. For hold timing, the analysis is a bit different. It checks that the data remains stable long enough after the clock edge.
![image](https://github.com/user-attachments/assets/048b9de3-deff-4d4d-8dfa-67f0462e9383)

The basic condition is θ > H, meaning the combinational delay must be greater than the hold time. But in real clocks, we again include the delay paths, so the equation becomes (θ + ∆1) > (H + ∆2). This ensures data is correctly latched at the capture flip-flop. 
![image](https://github.com/user-attachments/assets/8fbf7a75-865b-4200-a197-a691a5ebb709)


## Hold timing analysis using real clocks 
![image](https://github.com/user-attachments/assets/7614e52e-23a1-47c2-9554-73a56175326f)

For proper hold timing, the combinational delay must be greater than the hold time of the capture flip-flop. When the clock reaches the launch flip-flop, it passes through about two buffers (∆1), and when it reaches the capture flip-flop, it goes through around three buffers (∆2). Since both flops receive the clock from the same source, the clock uncertainty is the same for both. Adding this uncertainty, we analyze the timing by checking the slack, which is the difference between data arrival time and data required time. Slack should always be positive or zero—if it's negative, it indicates a violation.the timing paths from design, with single clock

![image](https://github.com/user-attachments/assets/65896c0c-c80b-443c-86bc-4cb355f1742c)

 
# LAB DAY 4
### 1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
commands:

![50 pic](https://github.com/user-attachments/assets/6e2d808c-b64c-4213-8bd4-493dc2618911)


tracks.info of sky130_fd_sc_hd

![51 pic](https://github.com/user-attachments/assets/d1307430-4457-4561-a024-d8739f0cb5ce)

commands for tkon window:

![52 pic](https://github.com/user-attachments/assets/935ed670-cf22-415a-96d2-ad0afc19a43b)

i/p and o/p ports of std cell lie on the intersection of vertical and horizontal tracks

![53 pic](https://github.com/user-attachments/assets/01151fd6-2fdf-450a-9501-1d9542a580c3)

calculations:
![53 1 pic](https://github.com/user-attachments/assets/bc93ddab-9e30-4290-8949-f7eeec08a062)
### Horizontal Track Pitch: 0.46 um
### Vertical Track Pitch:0.34 um
### Width of Standard Cell: 1.77 um
### Height of Standard Cell: 3.28 um

### 2.Save the finalized layout with custom name and open it.
![53 1 pic](https://github.com/user-attachments/assets/933bbe29-1204-4abc-a683-d75e87979bbc)

command to open newly opened layout:

![54 pic](https://github.com/user-attachments/assets/75d1b606-aacf-4cd5-9bfb-e3120ddeb9da)

new layout:

![55 pic](https://github.com/user-attachments/assets/5d961e89-8c0b-4a05-8924-0eb5c0be20ca)

### 3.Generate lef from the layout.
command at tkon window:
![56 pic](https://github.com/user-attachments/assets/197faf93-785d-434b-97c0-cee3f0df1aff)

newly created lef:
![57 pic](https://github.com/user-attachments/assets/96922d7c-618c-4f9f-b1d9-8a074db14a97)

### 4.Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
commands:
![58 pic](https://github.com/user-attachments/assets/e9f08270-d3c5-41ef-b2ee-2b90c5b0b3fc)

### 5.Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
![59 pic](https://github.com/user-attachments/assets/8823c29c-b5da-422c-ba16-5d9c220e3f23)

### 6.Run openlane flow synthesis with newly inserted custom inverter cell.
![60 pic](https://github.com/user-attachments/assets/ecc498fd-8645-407e-96cd-3949a557729d)
![61 pic](https://github.com/user-attachments/assets/3fbe3dee-a2ff-43ec-9217-366eba2acf99)
![63 pic](https://github.com/user-attachments/assets/b0be4e7e-9562-4fdc-a1b9-e661f28ebf5a)

### 7.Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
![62 pic](https://github.com/user-attachments/assets/336e62c2-9fc9-4486-af79-9f9d408dd245)
![63 pic](https://github.com/user-attachments/assets/b621bcae-06e0-407e-8933-52d0eeb12c8f)

image of merged.lef in tmp directory:
![64pic](https://github.com/user-attachments/assets/06a38b8b-fdb4-43a6-85a8-17d0e6273aa8)

commands to view and chnge parameters to improve timing and run synthesis:
![65 pic](https://github.com/user-attachments/assets/83c41a63-8068-488f-a756-c3e567ff842b)
![66 pic](https://github.com/user-attachments/assets/f77e39d9-3c6f-4e86-a4b9-0e37ccb8e6f2)
![67 pic](https://github.com/user-attachments/assets/ea9f8dca-5043-4031-bc75-3c805e08fab6)
![68 pic](https://github.com/user-attachments/assets/d88971b5-6621-4ab1-b739-92a3290a730b)

### 8.Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
![69 pic](https://github.com/user-attachments/assets/dde79d92-925e-468e-acb7-afd43c73bfd7)
![70 pic](https://github.com/user-attachments/assets/4ad7393e-fbdd-4b87-8090-f66f1b630024)

it shows error.so we use following commands and run it(shown the screen shot of commands run:
![71 pic](https://github.com/user-attachments/assets/d0a3f3ac-d48f-4a95-a15b-dbd9fc8e9537)
![72 pic](https://github.com/user-attachments/assets/2fb54b9a-70ad-4969-aafb-0e0f3f15a25c)
![73 pic](https://github.com/user-attachments/assets/96636d2c-3b7a-48ac-a959-73a8c79d87c0)
![74 pic](https://github.com/user-attachments/assets/f8c79fc7-dba2-46cf-8437-a8e64a53ce46)
![75 pic](https://github.com/user-attachments/assets/a5e4ba4e-8740-47be-858f-177bda76efba)

Commands to load placement def in magic in another terminal

![76 pic](https://github.com/user-attachments/assets/9eac715d-c9d2-4af2-9c39-d2f31b1ea012)

placement def in magic
![77 pic](https://github.com/user-attachments/assets/048de0a8-e978-4731-b7e4-9c705b4fdcb1)

screenshot showing a custommade inverter placed correctly inside the chip layout, lined up neatly next to other cells
![78 pic](https://github.com/user-attachments/assets/afb7918f-bb28-4387-8c48-a0ee9b6ba4a4)

to view internal layers of cells:

![79 pic](https://github.com/user-attachments/assets/5972d9da-26c4-43d9-a32e-6d964cd0f1a8)
![80n pic](https://github.com/user-attachments/assets/994bf796-2228-4689-a429-b8f1c0d4e89f)

### 9.Do Post-Synthesis timing analysis with OpenSTA tool.

![81 pic](https://github.com/user-attachments/assets/0fce1ea0-e86d-4be3-ac91-85b580226adb)
![82 pic](https://github.com/user-attachments/assets/361a9fad-cf30-4643-8c5e-43ffa34e41d9)
![83 pic](https://github.com/user-attachments/assets/01070ed3-de43-4de3-a05b-ce3fb3e1f6b1)

Nwwly created pre_sta.conf for STA analysis in openlane directory
![84PIC](https://github.com/user-attachments/assets/7312084e-f931-406d-8692-76964f1244eb)

Newly created my_base.sdc for STA analysis
![85PIC](https://github.com/user-attachments/assets/26b64ec0-0159-498f-b37b-a0fc8f43dc4b)

Commands to run STA in another termina
![115 pic](https://github.com/user-attachments/assets/28a66e84-78ed-4d4f-ae9e-f18efd0ec79e)
![116 pic](https://github.com/user-attachments/assets/dbb1db09-0861-4660-bcef-b9a96b262275)
![117pic](https://github.com/user-attachments/assets/62fef49e-0d48-4dc9-b219-fa03cf02f2f0)

Since more fanout is causing more delay we can  add parametr to reduce fanout and do synthesis again
![118pic](https://github.com/user-attachments/assets/93dbe550-d5da-44d4-9318-b2e736140ef0)
![119pic](https://github.com/user-attachments/assets/33b4dd17-aeed-4620-887f-c8175a996d02)

Commands to run STA in another termina
![120pic](https://github.com/user-attachments/assets/233141bf-17af-4f22-9de8-07bd8c1483b4)
![121pic](https://github.com/user-attachments/assets/6e13535a-c2a6-429b-b2d8-7146efc9c243)
![122pic](https://github.com/user-attachments/assets/6d0e8305-8e09-4f2e-9d74-cbf31a9e05ca)

### 10.Make timing ECO fixes to remove all violations.
OR gate of drive strength 2 is driving  4 fanout
![123pic](https://github.com/user-attachments/assets/326cd5b5-5f0e-4352-8bd2-05562de307a7)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
![124pic](https://github.com/user-attachments/assets/88304136-5805-4ed5-90ee-916b825e7685)
![125pic](https://github.com/user-attachments/assets/083cbba1-f2ab-4b29-a507-f25d4236e47f)
![128pic](https://github.com/user-attachments/assets/7e72ebc6-cb6c-454e-999a-370428840432)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
![129pic](https://github.com/user-attachments/assets/5ea320f0-f57f-4a1e-95a5-e00e67668f9f)
![130pic](https://github.com/user-attachments/assets/5131ac0e-2dab-428a-9df7-637586936986)
![131pic](https://github.com/user-attachments/assets/763ce382-a884-40c0-a604-eac5649cea13)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
![132pic](https://github.com/user-attachments/assets/fd170bad-f31f-4545-a5dd-499629cc9313)
![134pic](https://github.com/user-attachments/assets/08f489e0-7d42-4f1a-8d6a-51157446663a)
![135pic](https://github.com/user-attachments/assets/e0bbc4d2-731b-4901-93ab-644c31a4cb5a)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

![136pic](https://github.com/user-attachments/assets/3746fc91-ce88-4783-b0fa-76b5d22fe4b8)
![137pic](https://github.com/user-attachments/assets/eda8146d-289b-43fb-87fb-cae767a38b9d)

Commands to verify instance _14506_ is replaced with sky130_fd_sc_hd__or4_4

report_checks -from _29043_ -to _30440_ -through _14506_

![138pic](https://github.com/user-attachments/assets/14be0b93-4b24-4980-842b-8ab1b389a25e)



### 11.Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
![139pic](https://github.com/user-attachments/assets/071506c5-9573-4f5b-aba8-f1f0ec13151e)
###.Post-CTS OpenROAD timing analysis.

###.Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.




# sky130 Day 5-final steps for RTL2GDS using tritonRoute and openSTA
## Routing and design rule check (DRC) 

## Introduction to Maze Routing -Lee’s Algorithm
![image](https://github.com/user-attachments/assets/35e7c316-01a2-4426-a7b4-b5a1905adfce)

In the final stage of physical design, called routing, we aim to connect two points—source and target—using the shortest and most efficient path with minimal bends. One popular technique used is Maze Routing based on Lee’s Algorithm.

![image](https://github.com/user-attachments/assets/05cc877e-040a-4001-804b-115ce45eefa1)

In this method, the routing area is divided into a grid, and the algorithm searches for the best path using only horizontal and vertical moves—diagonal moves are not allowed.

![image](https://github.com/user-attachments/assets/fb2e0060-cb06-46d8-bff9-26082083156a)
![image](https://github.com/user-attachments/assets/da79a367-69a5-407b-b11d-dd3a73ba9d84)


Starting from the source point, the algorithm labels all reachable neighboring grids step by step with increasing integers until it reaches the target. Once the target is labeled, it traces back the shortest path, ideally forming 'L' or 'Z' shaped routes to avoid unnecessary twists.mostly prefers 'L' type because only 1 bend is present.

![image](https://github.com/user-attachments/assets/7bb7fdc4-d7d4-4852-ad39-579a41c5d32b)
![image](https://github.com/user-attachments/assets/fd45e4fc-d6eb-49a8-9605-32f5442edcac)


This process ensures clean, efficient routing with minimal complexity, avoiding zig-zag paths. Multiple examples follow the same approach, helping to visualize and understand the method clearly. 
![image](https://github.com/user-attachments/assets/37b8ed7e-e813-4ce8-8f56-90369615594d)
![image](https://github.com/user-attachments/assets/33ebf8ff-104f-44ed-b617-ca69bff48483)

## Design Rule Check 

Before performing Design Rule Check (DRC), we need to follow a process called DRC cleaning, which ensures that our circuit meets all fabrication rules. For example, when placing two parallel wires, there must be a minimum required distance between them to prevent issues.

the steps are:

1.the wire width should meet the minimum size based on the lithography technology used
![image](https://github.com/user-attachments/assets/994cece0-ee61-4f8f-a57e-a41ef7212677)

2.the wire pitch, which is the center-to-center distance between two wires, must also meet a specific minimum
![image](https://github.com/user-attachments/assets/1b6a75e9-a1fa-456f-b8f9-ff3c615f7845)

3.the wire spacing, or gap between the edges of two wires, must follow certain limits.
![image](https://github.com/user-attachments/assets/bacc1258-48ba-4280-8c14-6f856d45fd62)


In some cases, like when signals get shorted, the solution is to move one wire to a different metal layer—usually an upper layer that’s wider. it leads to additional checks, that are ** via width **( which must not be below a certain size) and ** via spacing ** (which also must meet minimum distance rules). After routing and DRC cleaning, the final step is parasitic extraction, where we calculate the resistance and capacitance of the wires, which is essential for accurate circuit analysis and further processing. 

![image](https://github.com/user-attachments/assets/74305480-1021-4a3f-a62a-27840a100aa5)
![image](https://github.com/user-attachments/assets/e344431b-0442-4e0d-a3ec-a75d32e8819f)

## Power Distribution Network and routing 


## Basics of global and detail routing and configure TritonRoute 

routing process is divided into two main stages: Global Routing and Detailed Routing.
![image](https://github.com/user-attachments/assets/a6426fa7-9313-477e-8c8c-d091e1a31d52)

In global routing, the chip layout is divided into rectangular grid cells, forming a 3D routing graph, and this step is handled by the FastRoute engine.in detailed routing, is done by the TritonRoute engine which finalizes the exact wire paths. For example, pins A, B, C, and D are connected to form a net through this process, ensuring all connections are accurately made on the chip. 


## TritonRoute Features 

## TritonRoute feature 1 - Honors pre-processed route guides 
![image](https://github.com/user-attachments/assets/c60addae-7408-4505-a25f-4d820633c2a7)

The initial detailed routing step follows the route guides that were created during the fast routing stage. These route guides act as a blueprint, showing where each wire should go. To work properly, these guides must meet a few conditions  1) they should have a uniform width, 2) follow the preferred routing direction for each layer, and ensure that all parts of a net are connected.  2guides are considered connected if they either touch on the same metal layer or overlap vertically on adjacent layers. The detailed router uses a smart technique called MILP-based panel routing, where  routing happens in parallel within a layer and sequentially between layers, helping to make the process more efficient and organized. 

## TritonRoute Feature2 & 3 - Inter-guide connectivity and intra- & inter-layer routing 

![image](https://github.com/user-attachments/assets/4fbd795a-e382-41aa-801b-33ae84d43fa8)

In detailed routing, every unconnected pin of a standard cell must be covered by a route guide to ensure it gets properly connected. As shown in the image, the black dots represent cell pins, and these are overlapped by the route guides, especially when the pins are placed at the intersection of vertical and horizontal routing tracks. This overlap helps ensure correct routing. The routing strategy used here is called intra-layer parallel and inter-layer sequential panel routing. "Intra-layer" means routing happens within a single metal layer, and "inter-layer" means it occurs between different layers. For example, looking at Metal 2 (M2), which has vertical routing, the layer is divided into strips called panels. Routing is done in parallel across panels with even indices first, then in the odd ones, all within the same layer. This pattern is repeated layer by layer—like in Metal 3 (M3)—where panels are also routed in parallel, first in the even panels (shown in part b) and then in the odd panels (shown in part c), completing the routing in a structured and efficient way. 

## TritonRoute method to handle connectivity  

![image](https://github.com/user-attachments/assets/0a9ea93a-a47c-4fe6-b616-1f857c626990)

In detailed routing, the input is the LEF file, and the output is a complete routing solution that aims to minimize wire length and the number of vias. This process must follow several constraints, such as sticking to the provided route guides, ensuring all connections are made properly, and following the design rules. To manage connectivity, the router works within a defined routing space and usef specific points called Access Points (APs)those are grid aligned spot on metal layers used to connect wires either to other layers, to pins, or to IO ports. A group of these related access points is called an Access Point Cluster (APC), and it collects all APs tied to the same source, like a pin or guide. The pic shows examples of access points connecting to (a) a lower-layer segment, (b) a pin, and (c) an upper-layer segment, helping ensure smooth and rule-compliant routing throughout the design. 

##Routing topology algorithm and final files list post-route 
![image](https://github.com/user-attachments/assets/b806c4b8-0c11-4b86-86b1-8871030b2a20)

To complete detaild routing efficiently, the algorithm calculates the cost of each Access Point Cluster (APC) and then finds the best connections by building a minimum spanning tree between them. This helps in selecting the optimal routing paths. 

 

 # LAB DAY 5
 
### 1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
commands:
![86PIC](https://github.com/user-attachments/assets/354798d9-18ce-452e-bd47-7d616309320c)

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

set ::env(SYNTH_STRATEGY) "DELAY 3"

set ::env(SYNTH_SIZING) 1

run_synthesis

![87PIC](https://github.com/user-attachments/assets/872bb687-1fe3-4708-9555-3af39bed80d6)
![88 PIC](https://github.com/user-attachments/assets/28c8fb78-2ed3-4792-a590-22c7cf55dfe3)

init_floorplan

place_io

tap_decap_or

![89 PIC](https://github.com/user-attachments/assets/9224d85f-badf-4ff2-9202-5eac70918cc5)

run_placement

![91 PIC](https://github.com/user-attachments/assets/8718749f-37e9-43c3-a0c2-efa70f347851)

unset ::env(LIB_CTS)

run_cts

![92 PIC](https://github.com/user-attachments/assets/a6d33a94-af78-421a-980d-fa93c9dcdb1d)

gen_pdn
![93 PIC](https://github.com/user-attachments/assets/74f3d36b-4ae6-4e72-baff-42f40c119ee1)
![94 PIC](https://github.com/user-attachments/assets/c5c141b3-8e57-4455-a166-14db7c692882)

commads to load PDN def in magic:
![95 PIC](https://github.com/user-attachments/assets/7ff48ab8-27c3-4c35-a320-2da3e8272093)

output:
![96 PIC](https://github.com/user-attachments/assets/fa4e7f9a-0499-45a2-b626-0f36f50fd96e)
![97 PIC](https://github.com/user-attachments/assets/c107c138-e84a-4723-9b02-4c4e1275d338)
![98 PIC](https://github.com/user-attachments/assets/3c4bceb5-a9ea-4ec3-b0a9-41d303597fde)

### 2. Perfrom detailed routing using TritonRoute.
![99 PIC](https://github.com/user-attachments/assets/29ef5d91-d2a1-460f-8ac5-8dfd154b5d83)
![100 pic](https://github.com/user-attachments/assets/27f37209-5083-477a-a6b3-c1c50d9755eb)
![101 pic](https://github.com/user-attachments/assets/e9cade94-1faa-47d9-8da3-d26f4a761574)

### 3.Commands to load routed def in magic in another terminal
![102 pic](https://github.com/user-attachments/assets/d7862df3-23b2-4100-ad23-a8eb7aff6873)
![103 pic](https://github.com/user-attachments/assets/21886220-9267-4c17-a80e-0e22760ce2bb)
![104 pic](https://github.com/user-attachments/assets/f081d145-765c-4c81-a38c-ff2b388dcd0b)
![105 pic](https://github.com/user-attachments/assets/82b9a5e9-a633-4817-8c1e-ed971b04097f)
![106 pic](https://github.com/user-attachments/assets/9003476d-19d1-4a48-b402-a3fa2bdc5c34)

fast route guide screenshot:
![107 pic](https://github.com/user-attachments/assets/a56fd24a-3463-4272-99dd-f01cdc2adf21)


### 4.Post-Route parasitic extraction using SPEF extractor.
Commands for SPEF extraction using external tool:

cd Desktop/work/tools/openlane_working_dir/openlane/scripts/spef_extractor/

python3 main.py \-l /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-06_13-00/tmp/merged.lef \-d /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-06_13-00/results/routing/picorv32a.def

![109 pic](https://github.com/user-attachments/assets/7a7dd60a-0c61-407e-bbf0-36503878effe)


### 5.Post-Route OpenSTA timing analysis with the extracted parasitics of the route.
### Command to run OpenROAD tool
openroad

### Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef

### Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def

### Creating an OpenROAD database to work with
write_db pico_route.db

### Loading the created database in OpenROAD
read_db pico_route.db

### Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/synthesis/picorv32a.synthesis_preroute.v

### Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

### Link design and library
link_design picorv32a

### Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

### Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

### Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.spef

### Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

### Exit to OpenLANE flow
exit

![110 pic](https://github.com/user-attachments/assets/10706b86-c16a-4a42-ae55-2c53f6b8f356)
![111 pic](https://github.com/user-attachments/assets/a5c1cf62-6d7c-497d-9dce-c5b8ffa87888)
![112 pic](https://github.com/user-attachments/assets/b3c96b26-859d-4d67-b1c4-5c493fc47919)
![113pic](https://github.com/user-attachments/assets/b2530b4a-ef78-406c-ba6b-c1a55ae4840f)
![114pic](https://github.com/user-attachments/assets/99510d32-e9bc-478d-841c-63831f8c6149)





## Acknowledgements

Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd.

Nickson P Jose, Physical Design Engineer, Intel Corporation.R. 

Timothy Edwards, Senior Vice President of Analog and Design, efabless Corporation.
