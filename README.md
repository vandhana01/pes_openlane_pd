# pes_openlane_pd
Advanced Physical Design using OpenLANE/Sky130

<p align="center">
<img width="700" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/1694b272-1d44-496e-acd1-7bfe96a40d27">
</p>

 ## OVERVIEW
- Advanced Physical Design in the context of OpenLANE and SkyWater 130nm (Sky130) process technology is a sophisticated approach to optimizing integrated circuits. It involves the meticulous refinement of digital ASICs to meet stringent **performance, power, and area (PPA) requirements**. Leveraging OpenLANE, an open-source digital ASIC flow, engineers can automate and streamline the intricate process of design, synthesis, placement, routing, and verification. 

   - **Open-source EDA Tools:** Open-source EDA tools are software applications and libraries that are freely available and collaboratively developed by the open-source community. These tools provide the essential infrastructure for designing integrated circuits and semiconductor devices. The open-source nature of these tools promotes accessibility, transparency, and innovation within the field of digital design.
   
   - **OpenLANE:** OpenLANE is an advanced open-source digital ASIC (Application-Specific Integrated Circuit) design flow that streamlines the process of creating custom chips. It integrates a variety of EDA tools and automation scripts into a unified platform, allowing designers to take a design from RTL (Register Transfer Level) to GDSII (Graphics Database System II) without the need for expensive commercial EDA tools. OpenLANE has become a crucial tool in making ASIC design more accessible and cost-effective.
   
   - **Sky130 PDK:** The Sky130 Process Design Kit (PDK) is an open-source collection of files, libraries, and data that defines the manufacturing process for a 130nm semiconductor technology. Developed by the SkyWater Technology Foundry, this PDK is unique in its open-source nature, making it available to a broad range of users, including startups, researchers, and hobbyists. It includes information about standard cells, IO pads, technology files, and design rules, allowing designers to create chips using the Sky130 process.
     
- This advanced methodology enables the creation of highly efficient and reliable integrated circuits, making it a vital component of modern semiconductor engine.
       
# **Setup Environment**
- Ensure you have a suitable Linux-based environment with the necessary dependencies installed.
- Clone the OpenLANE repository from GitHub and set up the environment as per the provided documentation.
   - https://openlane.readthedocs.io/en/latest/getting_started/installation/installation_ubuntu.html#
- Refer to "StepsToDownloadAndInstallEDATools" file in materials folder.

  
# **Contents**  
## DAY 1
<details>
<summary> Inception of open-source EDA,openLANE and Sky130 PDK </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)

- [Introduction to QFN-48 Package,chip,pads,core,die and IPs](#Introduction-to-QFN-48-Package,chip,pads,core,die-and-IPs)
- [Introduction to RISC-V](#Introduction-to-RISC-V)
- [From Software Applications to Hardware](#From-Software-Applications-to-Hardware)
- [Introduction to all components of open-source digital asic design](#Introduction-to-all-components-of-open-source-digital-asic-design)
- [Simplified RTL2GDS flow](#Simplified-RTL2GDS-flow)
- [Introduction to openLANE and strive chipsets](#Introduction-to-openLANE-and-strive-chipsets)
- [Get familiar to open-source EDA tools](#Get-familiar-to-open-source-EDA-tools)

# How to talk to computers

## Introduction to QFN-48 Package,chip,pads,core,die and IPs

<img width="350" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/e9269d03-a16b-4512-a564-5947e9bbe083">
-->

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/87f0f3fb-5807-4b9b-9d21-fa4533899759">

- QFN-48(Quad Flat No-Lead 48) package is a commonly used IC packaging format known for its compact size and thermal efficiency.
- Within this package, several crucial components play distinct roles in the functioning of an electronic device:
  
- **QFN-48 Package**
   - The QFN-48 package refers to the physical housing that encases an integrated circuit.
   - It features a flat, square or rectangular shape with a set number of external pins or leads for electrical connections.
   - The "48" in QFN-48 indicates the total number of pins on the package.
<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/39244da7-99c7-4d70-9ade-6ea1279a2859">


- **Chip**
   - The chip, also referred to as the integrated circuit (IC) or die, represents the heart and brains of the electronic device.
   - This tiny silicon wafer contains intricate semiconductor components, including transistors, resistors, and capacitors, arranged to execute specific functions as per the device's design and intended application.
   - The chip is encapsulated within the QFN-48 package.
<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/b1b49058-3fc8-4bc5-84c4-af02f731348f">

- **Pads**
   - On the underside of the QFN-48 package, an array of metallic pads is arranged. 
   - These pads function as the electrical interface between the IC inside the package and the external circuitry, typically a printed circuit board (PCB).
   - Each pad connects to a specific function, such as power, ground, input, or output, facilitating communication between the IC and the external world.

- **Core**
   - Within the chip (IC or die), the core represents the central processing unit (CPU) or primary computational engine.
   - It is the heart of the IC and is responsible for executing program instructions, performing calculations, and managing data flow.
  
- **Die**
   - Die refers to a small, individual piece of silicon that contains the electronic components of a single IC or semiconductor device.
   - Each die plays a critical role in the overall functionality of the semiconductor device it is a part of.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/0250d075-b6a3-4d2c-a180-27fc0cdb12e1">


- **IPs**
   - Intellectual properties (IPs) are modular components that can be integrated into the chip's design to add specific functions, making the overall design process more efficient and cost-effective.
   - **Foundries** play a crucial role in the semiconductor industry by providing semiconductor manufacturing services to companies that design ICs but do not have the facilities or expertise to produce them in-house.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/67250a83-35b4-4b38-9ba9-8c9c1fafb7b0">

## Introduction to RISC-V
- The RISC-V Instruction Set Architecture (ISA) is an open and royalty-free standard ISA for designing efficient and scalable computer architectures.
- Open Standard: RISC-V is an open and royalty-free ISA managed by a consortium, allowing anyone to implement it without licensing fees.
- Modular Design: It offers different instruction sets and optional extensions for diverse applications, promoting flexibility.
- Simplified ISA: Following the RISC philosophy, it features a streamlined and orthogonal instruction set for efficient hardware design and compiler optimization.
- Scalability: RISC-V scales from small embedded devices to high-performance systems with 32-bit, 64-bit, and 128-bit address spaces.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/2754a35c-e95a-420c-99eb-97ec7a56fff0">


## From Software Applications to Hardware

The flow you've outlined represents the layers and components of a typical computing system, starting from the highest level of application software down to the underlying hardware. Here's a more detailed breakdown of this flow:

1. **Application Software:**
   - Application software refers to the programs and applications that users interact with directly. These software applications serve specific purposes, such as word processing, web browsing, gaming, or data analysis. Examples include Microsoft Word, Google Chrome, and Adobe Photoshop.

2. **System Software:**
   - System software serves as an intermediary between application software and hardware, providing essential services and managing system resources. It includes several components:
   
   - **Operating System (OS):**
     - The operating system is a fundamental piece of system software that manages hardware resources, provides a user interface, and offers services for application software. Examples include Windows, macOS, and Linux.

   - **Compiler:**
     - Compilers are software tools that translate high-level programming languages (e.g., C++, Java) into machine code or low-level languages that can be executed by the computer's hardware. They are crucial for software development.

   - **Assembler:**
     - An assembler is a tool that translates assembly language code into machine code. Assembly language is a low-level representation of instructions that can be directly executed by the computer's central processing unit (CPU).

3. **Hardware:**
   - Hardware represents the physical components of the computer system. This layer includes various components such as the CPU, memory (RAM), storage devices (hard drives, SSDs), input/output devices (keyboard, mouse, monitor), and peripheral devices (printers, scanners, etc.).

The flow reflects the hierarchical structure of a computing system, with each layer building upon the one below it. Application software relies on system software to interact with and control hardware resources. System software, in turn, depends on the hardware to execute its functions. This layered approach is essential for the proper functioning of modern computer systems and ensures a separation of concerns between different levels of software and hardware.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/6b8bc141-2373-48cb-b474-e7e653954843">


# SoC design and OpenLANE 


## Introduction to all components of open-source digital asic design
The open-source approach aims to democratize and make ASIC design more accessible to a broader community of engineers and designers, fostering innovation and collaboration.

<img width="562" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/66044ce1-88f0-4aa2-823a-305a88cd9925">

## Simplified RTL2GDS flow
Register Transfer Level to Graphic Data System flow is a complex and multi-step process used to design and fabricate integrated circuits (ICs).

- **RTL (Register Transfer Level)**:
   - RTL is a level of abstraction in digital circuit design that represents the functionality and behavior of a digital system. It describes how data flows through registers and how logical operations are performed within a digital circuit.Designers create RTL descriptions using hardware description languages (HDLs) like VHDL or Verilog.
- **GDS (Graphics Database System)**:
   - GDS is a file format and a set of tools used for representing and manipulating the physical layout of integrated circuits. GDS files contain information about the position, shape, size, and connectivity of all the components and interconnects on a semiconductor chip.   

<img width="563" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/4a0ce8ae-d33c-4933-aade-30353270990f">


- **Synthesis**
   - Converts RTL to a circuit out of components from the standard library (SCL)
   - In this stage, tools like Synopsys Design Compiler or Yosys generate a gate-level netlist, which consists of standard cells, flip-flops, and logic gates (AND, OR, flip-flops, etc.) and their interconnections.
- **Floor and Power Planning**
   - Floor planning is the initial phase of physical design where designers allocate space on the chip's layout for different functional blocks, such as the CPU core, memory, input/output (I/O) pads, and other components.
      - Ensure efficient utilization of silicon area.
      - Optimize for performance, minimizing signal delays
   - Power planning involves the distribution of power and ground signals across the chip to ensure that all components receive stable and adequate power supply while minimizing power consumption and heat generation.
      - Ensure a reliable power supply to all parts of the chip.
      - Minimize voltage drops and IR (current * resistance) losses.
   - Both floor planning and power planning are iterative processes that require collaboration between different design teams to meet performance, power, and thermal objectives while adhering to the chip's area and manufacturing constraints. These processes are fundamental to achieving a successful physical design for semiconductor chips.
- **Placement**
   - The process of determining the physical locations of various components and elements on the chip's layout. 
   - Effective placement is crucial for achieving a successful chip design. It sets the stage for subsequent steps in the design flow, including routing and physical verification. Achieving a well-balanced placement that meets the design's performance and power goals while adhering to design rules is a key challenge in IC design.
      - Global Placement: This phase defines approximate locations for components and considers high-level objectives like chip symmetry and resource allocation.
      - Detailed Placement: In this phase, fine-grained placement decisions are made to optimize for performance and meet specific constraints.
- **Clock Tree Synthesis (CTS)**
   - It is the process of creating an optimized and balanced distribution network for clock signals throughout the chip.
   - The primary goal of CTS is to ensure that all sequential elements, such as flip-flops and latches, receive clock signals with minimal skew and jitter, enabling synchronized and reliable operation of the entire circuit
   - CTS begins with the design of the clock network, which includes the creation of a tree-like structure of buffers and wires to distribute the clock signal from a single source (the clock input) to all clocked elements in the chip.
- **Routing**
   - It involves the creation of interconnections or wiring that connect various components, such as logic gates, flip-flops, and memory cells, on the semiconductor chip's layout.
   - Routing often takes place on a grid-based system, where wires are placed on a grid of rows and columns. This simplifies the routing process and aligns wires neatly.
   - Specialized routing algorithms and tools are employed to automate and optimize the routing process while meeting design, performance, and manufacturing requirements
- **Sign Off** 
   - **Physical Verification:**
      - **Definition:** Physical verification, also known as design rule checking (DRC) and layout versus schematic (LVS) verification, involves a series of checks to ensure that the chip layout conforms to the design rules specified by the semiconductor foundry and design team.
   
      - **Design Rule Checking (DRC):** DRC involves checking the chip layout for violations of geometrical and physical constraints, such as minimum feature size, clearances, spacing, and alignment rules. It ensures that the layout can be reliably manufactured.
   
      -  **Layout Versus Schematic (LVS) Verification:** LVS verification compares the actual layout of the chip to the original schematic design to verify that they match. It checks for discrepancies in the connectivity and electrical properties of the components.
   
   - **Timing Verification:**
      - **Definition:** Timing verification, often referred to as static timing analysis (STA), is the process of rigorously analyzing the chip's design to ensure that it meets timing constraints, such as setup time, hold time, and maximum clock frequency.
   
      - **Static time analysis:** STA involves a detailed and precise analysis of the timing behavior of the digital circuit to ensure that it meets timing constraints and operates correctly. 

   - Both physical verification and timing verification are critical to ensure that semiconductor chips meet manufacturing and performance specifications. These processes are iterative, and adjustments are made to the design until all checks pass and timing requirements are met.
  
## Introduction to openLANE and strive chipsets
- Problem is tougher when using open source EDA : Tools Qualification? Tools Calibration? Missing Tools?
- **OpenLANE** : OpenLANE is an open-source EDA toolchain that facilitates the automated design and verification of digital chips, specifically ASICs
   - Produce a clean ( No LVS Violations, No DRC Violations and Timing Violations) GDSII with no human intervention.
   -  tape-out-hardened flow that addresses two main use cases: hardening a macro and integrating a System-on-a-Chip (SoC)
   - Tuned for SkyWater 130nm Open PDK
   - Containerized : Functional out of the box , Instructions to build and run natively will follow
   - Modes of operation: Autonomous or Interactive
     
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/c1680d96-d70a-4a7d-b046-1463ed3c215d)


OpenLANE flow consists of several stages. By default all flow steps are run in sequence. Each stage may consist of multiple sub-stages. OpenLANE can also be run interactively as shown [here][25].

1. *Synthesis*
    1. `yosys` - Performs RTL synthesis
    2. `abc` - Performs technology mapping
    3. `OpenSTA` - Pefroms static timing analysis on the resulting netlist to generate timing reports
2. *Floorplan and PDN*
    1. `init_fp` - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
    2. `ioplacer` - Places the macro input and output ports
    3. `pdn` - Generates the power distribution network
    4. `tapcell` - Inserts welltap and decap cells in the floorplan
3. *Placement*
    1. `RePLace` - Performs global placement
    2. `Resizer` - Performs optional optimizations on the design
    3. `OpenPhySyn` - Performs timing optimizations on the design
    4. `OpenDP` - Perfroms detailed placement to legalize the globally placed components
4. *CTS*
    1. `TritonCTS` - Synthesizes the clock distribution network (the clock tree)
5. *Routing*
    1. `FastRoute` - Performs global routing to generate a guide file for the detailed router
    2. `CU-GR` - Another option for performing global routing.
    3. `TritonRoute` - Performs detailed routing
    4. `SPEF-Extractor` - Performs SPEF extraction
6. *GDSII Generation*
    1. `Magic` - Streams out the final GDSII layout file from the routed def
    2. `Klayout` - Streams out the final GDSII layout file from the routed def as a back-up
7. *Checks*
    1. `Magic` - Performs DRC Checks & Antenna Checks
    2. `Klayout` - Performs DRC Checks
    3. `Netgen` - Performs LVS Checks
    4. `CVC` - Performs Circuit Validity Checks   
   - We put our HDL in at one end, and out the other comes the GDSII files that are the standard file format for the foundary.
   - This flow performs full ASIC implementation steps from RTL all the way down to GDSII based on several components including OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, CVC, SPEF-Extractor, CU-GR, Klayout and costum methodology scripts for design exploration and optimization. OpenLANE makes use of the efabless floorplanning script, makes use of the STA, placement, and routing in OpenROAD, and includes automated design space exploration
       
- **striVe** : OpenLANE was used successfully for the tape out of a family of RISC-V based SoCs called “striVe”. - Open PDK, Open EDA, Open RTL
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/ed34acb8-a1e7-4ce6-a8e7-6b34c9d7a342)

  
- OpenLANE is an open-source EDA toolchain that aids in the design and verification of digital chips, while Strive Chipsets are the customized semiconductor chipsets created using EDA tools like OpenLANE to address specific application or market needs. Together, they represent the intersection of open-source collaboration and customized semiconductor design for a wide range of industries and applications.

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f6a93f4d-a2cf-4795-b66d-5d35edefa68e)



# Get familiar to open-source EDA tools
## Skywater PDK Files
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/270c68db-60da-42d5-b145-bcc3e58b5510)


- There are three subdirectories
   - **Skywater-pdk**: Contains all the PDK related files
   - **Open_pdks**: Contains scripts that are used to bridge the gap between closed-source and open-source PDK to EDA tool compatibility
   - **Sky130A**: Compatible open-source PDK files
## Invoking OpenLANE
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/e78f5e0e-6274-45d9-b0fa-f878aa98b9c3)

- `flow.tcl` is the file that contains the script to run the designs
- `-interactive` - runs step by step process (interactive mode)
## Importing package
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/ffb3ac51-f674-461b-b3a8-d38daa6e15d7)


- `package require openlane 0.9` To import all the packages that are required to run OpenLANE
## OpenLANE design folder
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/ad58def0-b153-4153-a05e-48906c6cc034)

- All the designs run within OpenLANE are in design folder
## Hierarchy of Design folder
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/907d4200-9ca5-4d46-b715-6e575af85d4c)

Every design folder has_
- `Src folder` : Contains verilog files and sdc constraint files
- `Config.tcl files`: Design specific configuration switches used by OpenLANE
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/d963b90a-34db-43c6-aedc-4e80aa1a2ae0)

  -`less config.tcl` 
## Prepare the design
- To Setup files specific to the design flow
- `prep -design <design_name>`
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/7b58a64b-7c26-4a3a-87d3-1bde824003bd)

- After design prep , there will be a new run directory created ,where all the results will be stored. 
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/74e04fb3-4820-4a6e-842e-ec53a9c0e8ff)


 ## Synthesis
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/40af13a8-851e-4b9c-8964-98064f32a2d6)

- `run_synthesis`: To run synthesis
- After synthesis find the flop ration = No. of D flip flops / Total number of cells
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/cfccef6b-90f8-44db-b1fe-b25feb6eda86)

 
</details>

## DAY 2
<details>
<summary> Good floorplan vs bad floorplan and introduction to library cells </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)

- [chip Floor planning considerations](#chip-Floor-planning-considerations)
- [Library Binding and placement](#Library-Binding-and-placement)
- [Standard Cell design and characterization flow](#Standard-Cell-design-and-characterization-flow)
- [General timing characterization parameters](#General-timing-characterization-parameters)
  
# chip Floor planning considerations
1. **Utilizaton factor and aspect ratio**
   - Define Width and Height of Core (All logical cells are present)  and Die
   - Utilization factor measures how efficiently a chip's available area is used for active components
    - UTILISATION FACTOR = Area Occupied by the Netlist / Area of the core  (Normally 50-60% utilization)
   -  aspect ratio defines the chip's width-to-height ratio in the layout. Affect chip shape and manufacturing.
    - ASPECT RATIO = Height / Width (If it is =1 (square), else (rectangle) shape
2. **Pre-placed cells (Macros)**
   - Functional blocks  such as processor cores, memory blocks, mux,comparator, clock-gating cell or I/O interfaces.  
   - The arrangement of these IPs on chip is called Floorplanning
   - These IPs/blocks have user-defined locations and hence are placed in chip before automated placement and routing. Therefore called pre-placed cells.
   - Automated Placement and Routing tool places the remaining logical cells in the design onto chip.
3. **De-coupling capacitors**
   - Decoupling capacitors are small capacitors placed strategically on the power supply lines (VDD and VSS) of an electronic circuit or IC.
   - They store electrical energy when the voltage level is higher than required and release it when the voltage drops below the desired level (local reservoir of charge)
   - Hence **Local communication** is taken care as they stabilize power supplies by absorbing voltage fluctuations, reduce electrical noise, and ensure signal integrity
4. **Power planning**
   -  Power planning is crucial for reducing noise in digital circuits caused by voltage droop and ground bounce.
   -  Coupling capacitance forms between interconnect wires and the substrate, which charged or discharged to represent logic 1 or logic 0 states in the circuit.
   -  During signal transitions, charge associated with coupling capacitors may be released or "dumped" to ground resulting in transient voltage fluctuations and noise on the power and ground lines.
   -   If there aren't enough ground taps, charge can accumulate at these taps. This excess charge can cause the ground line to behave like a large resistor, leading to an increase in ground voltage and a reduction in noise margin.
    -  To address these issues, a **Global communication** i.e., robust power delivery network with numerous power strap taps is essential.  
5. **Pin placement and logical cell placement blockage**
   - Also known as I/O (input/output) pad placement, involves determining the locations and assignments of input and output pins on the chip's periphery.
   - Proper pin placement is crucial for efficient power distribution.
   - By creating **placement blockages** around the components, designers can ensure that they are physically isolated from other parts of the design, reducing the risk of interference or unwanted coupling. 
6. **Floorplan using OpenLANE**
- Before running floorplan, Check the available switches
  - ` cd Desktop/work/tools/openlane_working_dir/openlane/configuration`
  - `less README.md`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/9ab642a0-53dd-4739-a362-6c629a82cea4)

 - floorplanning will be run according to configuration settings in the design specific `config.tcl` file.
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/0c89fadc-1aac-4489-83c9-482e1d10e3d7)

 - `run_floor` in openlane to execute the floorplanning step.
 - an essential command in OpenLANE for creating the initial physical floorplan of an ASIC design. 
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f646d287-880b-43a4-8ba7-b90297b2dfcd)


 - Output is the `def` file  (design exchange format)
 - contains important information about the physical layout of the chip, including the positions and dimensions of cells, placement of I/O pads, the power grid structure, and other physical design details.
 
- `less picorv32a.floorplan.def`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f06a0d35-cc2e-4e82-8256-8338168ce178)


7. **Floorplan layout in Magic**
  - To see actual layout after floorplan
  - `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &`
  -  setting up the "magic" tool for the specified technology node, reading in a LEF file describing a standard cell library, and reading in a DEF file that likely contains the floorplan for an IC design based on the Picorv32 processor core.
  -  The "&" symbol at the end of the command allows you to run multiple commands in a single line
  
<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/d408af5f-a67c-4911-97dd-bd95b72296a5">  

# Library Binding and placement
-  They involve selecting and placing standard cells from a library onto the chip's floorplan. They provide the foundation for subsequent stages in the ASIC design flow, including routing, verification, and manufacturing preparation.
1. **Netlist binding and initial place design**
   - Library will have width and height of cells, delay/timing info, required conditions, various shapes gates, various flavours of cells, etc
   - Netlist binding, also known as cell binding or logic binding, is the process of associating logical functions or gates from a high-level RTL (Register-Transfer Level) design with specific standard cells or library cells from a cell library.
   - The primary goal of initial placement is to create a starting point for the detailed placement step. It provides a rough layout of cells on the chip, ensuring that critical paths are appropriately positioned and that power and clock distribution networks can be efficiently established.
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/511b4f02-863b-4368-b450-e91df83a5f1e">     


2. **Optimize placement**
   - Clearly define your optimization objectives, which may include minimizing wirelength, meeting timing constraints, optimizing for power distribution, and achieving area efficiency.
   - This is the stage where we estimate wire length and capacitance and based on that, insert repeaters(buffers that recondition the original signal and make a new signal and send it to following stage to maintain signal interigty)
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/8818e4a2-241f-4df9-b9de-a9f11794d91e">

   - timing analysis is done, assuming that all the clock signals are performing at ideal rate , to check wheather the placement done reasonable or not
    
3. **Placement**
- **Global Placement**: Initially, use global placement algorithms to provide a rough placement of cells. These algorithms consider high-level objectives and balance different goals. But not a legal placement
- **Detailed Placement**: Detailed placement refines the positions of individual cells, optimizing for local objectives, Legalize the cell placement, addressing timing and congestion issues.

  - `run_placement` : Global placement is performed
- `cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs`
- after `ls` follow up with `<data>` `results` `placement` `picorv32a.placement.def`
- `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &`
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/85a40839-663f-4944-b4ef-0f2046140f37">

Zoom in
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/c66b475e-7a65-4ab1-adca-269e94ea7fe0">

# Standard Cell design and characterization flow
- They are pre-designed and pre-characterized logic gates or functional blocks with fixed heights that are used to implement digital logic functions in an IC. 
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/2dde2399-1b39-440c-826d-333b1ad5764d">

- **Cell Design Flow** ___
  1. Inputs : Process design kits(PDKs), DRC & LVS rules, SPICE models, library and user-defined specs.
  2. Design Steps : Circuit Design, Layout Design, Characterization. The software GUNA used for characterization. The characterization can be classified as Timing characterization, Power characterization and Noise characterization.
  3. Outputs : CDL (Circuit Description Language), GDSII, LEF, extracted Spice netlist (.cir), timing, noise, power.libs, function.
     
- **Characterization flow**
    - These libraries, along with their associated Liberty files, play a key role in enabling synthesis tools to determine the optimal arrangement of standard cells in an IC design.
      
<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/8b801ae5-cd16-49e7-b831-1c76badea449">   

<img width="450" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/ecf665d3-fc89-42d0-9282-ed4887ae9442"> 

- **STEPS**
1. Read the module files
2. Read the extracted SPICE netlist
3. Recognise the behaviour of the buffer
4. Read sub-circuits of the inverter
5. Attach the necessary power supplies
6. Apply the stimulus
7. Provide necessary output capacitances
8. Provide necessary stimulation command

- The open-source software GUNA is used for characterization.
<p align="center">
<img width="500" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/35c83caf-db2b-444c-8976-40ee57df7863">
</p>


# General timing characterization parameters 
- **Timing threshold definitions**
-  `slew_low_rise_thr` : 20% from bottom power supply of a rising signal
-  `slew_high_rise_thr` : 20% from top power supply of a rising signal
-   `slew_low_fall_thr` : 20% from bottom power supply of a falling signal
-  `slew_high_fall_thr` : 20% from top power supply of a falling signal
-  `in_rise_thr` : 50% point on the rising edge of input
- `in_fall_thr` : 50% point on the falling edge of input
- `out_rise_thr` : 50% point on the rising edge of ouput
- `out_fall_thr` : 50% point on the falling edge of ouput

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/852c2282-0520-43b1-9b62-23f1197e715c"> 

- These are used to calculate factors such as propogation delay and transition time.
    - **propogation delay** = time(out_*_thr) - time(in_*_thr)
    - **Transition time** = time(slew_high_rise_thr) - time(slew_low_rise_thr) 
</details>

## DAY 3
<details>
<summary> Design library cell using Magic Layout and ngspice characterization </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)

- OpenLANE has the benefit of allowing changes to internal switches of the ASIC design flow on the fly. This allows users to experiment with floorplanning and placement without having to reinvoke the tool.
  - Can be done resetting the variable using `set <variable>`
  - Followed by running the flow again for the values to reset
  
- [Labs for CMOS inverter ngspice simulations](#Labs-for-CMOS-inverter-ngspice-simulations)
- [Inception of Layout CMOS fabrication process](#Inception-of-Layout-CMOS-fabrication-process)
- [Sky130 Tech File Labs](Sky130-Tech-File-Labs)
  
# Labs for CMOS inverter ngspice simulations
## SPICE Simulations
- SPICE (**Simulation Program with Integrated Circuit Emphasis**) is a widely used simulation tool for electronic circuit design and analysis.
- SPICE simulations are invaluable for verifying circuit functionality, assessing performance, and identifying potential issues before moving to the physical prototyping and manufacturing stages. 
- To simulate standard cells, first we should create spice deck wrappers around our model files.
    - SPICE deck will comprise of:
    - Model include statements
    - Component connectivity, including substrate taps
    - Output load capacitance
    - Component values
    - Node names
    - Simulation commands
      
<p align="center">
<img width="500" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/872548f7-032a-4360-b731-da50e2430719">
</p>   

## SPICE Deck creation and simulation for CMOS Inverter
## CMOS_inverter.cir
  - Drain Gate Source and Substrate format (connectivity info)
  - Should include the model file
    
```cir
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
Vin in 0 2.5

*** SIMULATION Commands ***
.op
.dc Vin 0 2.5 0.05

*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS
.end
```    
- To plot the output waveform of the spice deck we will use ngspice.
- The steps to run the simulation on ngpice are as follows:
     1. Source the .cir spice deck file: ` cd <file location>`
     2. Run the spice file by: run
     3. Run: setplot → allows you to view any plots possible from the simulations specified in the spice deck
     4. Select the simulation desired by entering the simulation name in the terminal
     5. Run: display to see nodes available for plotting
     6. Run:`plot a vs b`  to obtain output waveform

## Switching Threshold Vm
- SPICE Analysis
- CMOS cells have three modes of operation:
      1. Cutoff - No inversion
      2. Triode - Inversion but no pinchoff in channel
      3. Saturation - Inversion and pinchoff in channel
- The voltages at which the switch between the modes of operation happens is dependent on the threshold voltage of the device(s). Threshold voltage is a function of the W/L ratio of a device, therefore varying the W/L ratio will vary the output waveform of CMOS devices.

<p align="center">
<img width="500" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/e2b0c0c9-6d6e-4b53-8712-0a3e7eb854c4">
</p>   

- To enable efficient description of the varying waveforms a single parameter called **switching threshold** is used. Switching threshold(Vm) is defined at the intersection of Vin = Vout. A perfectly symmetrical device will have a switching threshold such that Vin = Vout = VDD/2. If it is not symmetric, try to increase the PMOS width and run the simulation again. 

## Dynamic simulation of CMOS
- Static simulations are used to analyze the behavior of a circuit under DC (direct current) conditions, typically to determine its DC operating point, voltage levels, and current flows.
- Dynamic simulations focus on the transient behavior of a circuit over time, such as how it responds to input changes.
- **For Dyanamic Simulation of CMOS inverter**
```cir
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
Vin in 0 0 pulse 0 2.5 0 10p 10p 1n 2n 

*** SIMULATION Commands ***
.op
.tran 10p 4n

*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS
.end
```   
# Inception of Layout CMOS fabrication process
## 16-Mask CMOS Process Steps
1. **Selecting a substrate**
   - Selection of base layer on which other regions will be formed.
   - P-type, high resistivity(5~50ohms) doping level (10^15 cm^-3) and orientation (100).
   -  substrate doping should be less than "well" doping (used to fabricate NMOS and PMOS)
2. **Create an active region for transistors**
   - Pockets created for NMOS and PMOS using photoresist and photolithography. 
   -  Grow SiO2 (~40nm) on P-type substrate. (create isolation between pockets)
   -  Deposit Si3N4 (~80nm) on SiO2
   -  Deposit ~1um layer of photoresist(used to define regions)
   -  photolithography(selectively exposing and chemically treating a photoresist, to create a pattern that is then transferred onto the wafer)
   -  etch out Si3N4 and SiO2 using a suitable solvent
   -  Place the obtained structure in oxidation furnace due to which field oxide is grown.This process is called LOCOS(Local oxidation of silicon)
   -  Etch out Si3N4 using hot phosphoric acid
3. **NWell and PWell formation**
   - create the n-wells and p-wells for PMOS and NMOS transistors, respectively
   - Apply photoresist and mask to cover NMOS/PMOS , expose to UV and remove mask. Perform Ion Implantation
   -  Pwell uses boron(~200keV) and nwell uses phosphorus(~400keV).
   -  depth of the wells will be is low. Therefore Drive in diffusion by placing it in a high temperature furnace to increases the well depth.
4. **Formation of Gate**
   - For desired threshold value NA (doping Concentration) and Cox to be set.
   - Repeat step 3 , But Pwell uses boron(~60keV) and nwell uses Arsenic
   - SiO2 will be damaged due to implantation, Soo Original oxide etched/stripped using dilute hydrofluoric(HF) solution
   - Then re-grown again to give quality oxide(~10nm thin)
   - Deposit polysilicon layer(~0.4um) and N-type (phosphorous or arsenic) ion implants for low gate resistance
   - again mask on small width of Nwell and PWell above SiO2 and perform photolithography
5. **Lighlt Doped Drain(LDD) Formation**
   - LDD done to avoid hot electron effect and short channel effect
   - To Nwell Create a mask, spin a photoresist,  phosphorous to make N-Implant on p-well(N-)
   - use boron to make P-Implant on n-well (p-)
   - Protect LDD by despositing ~0.1um Si3N4 or SiO2 and perform  plasma anisotropic etching that results in formation of side wall spacers    
6. **Source and Drain Formation**
   - Thin screen oxide to aviod channeling during implants
   - Mask, photoresist,wask, etch
   - Nwell structure, deposit arseni(~75KeV) that forms an N+ implant on Pwell and use boron(~50keV) for P+ implant formation on Nwell
   - Expose to high temperature furnace that results in required thickness of N+,P+,N-,P- implants.
7. **Steps to form contacts and interconnects**
   - SiO2 removed using HF etch. Titanium deposited using sputtering.
   - Wafer heated at about 650-700C in N2, ambient for 60sec . Results in low resistant TiSi and TiN which is used only for local communication
   - Etch off TiN on and half around gate structure of both MOS using RCA Cleaning
8. **Higher level metal formation**
   - 1um of SiO2 doped with phosphorous or boron(known as phosphosilicate glass or borophosphosilicate glass) deposited on wafer surface
   - chemial mechanical polishing(CMP) technique for planarizing wafer surface
   - Create contact pins by masking, photoresist, etching... and again do CMP
   - Aluminum layer deposition, tiN deposition , W as contacts, and masking, photoresist, etching... everytime . proper holes with contacts have to be made
   - Top dielectric(Si3N4) to protect the chip

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/d384aa4f-1546-4f14-87a0-5173e9f8e0a1)


# Sky130 Tech File Labs

## Magic Layout View of Inverter Standard Cell         
- Git clone : `https://github.com/nickson-jose/vsdstdcelldesign` for cell files
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/16c6b884-c376-439c-81ec-a4ddf7cec67b)

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/082ece10-bf75-49c6-b00b-d79226a3d749)


-  `cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag &`

<p align="center">
<img width="300" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/b405e246-1369-40d6-a134-e9916faa0c27">
</p>


- Magic Key Features:
   1. Color Palette - Defines layers and associated colors
   Continuous DRC
   2. Device Inference - Automatic recognition of NMOS and PMOS devices
      
- **Device Inference** :
- Select the specific layer/device by hovering over the object and pressing, s, iteratively, until you traverse the hierarchy to the specified object
- move the cursor to a required area, and press `s`
- Run the what command in the tkcon window:

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f9a02674-6519-46c9-9ee9-2d62182b2897"> 


## DRC errors
- Design Rule Check involves checking whether the layout design of an integrated circuit adheres to a set of predefined design rules and constraints.
- DRC errors in magic will be highlighted with white dotted lines:
- To identify DRC errors select `DRC find next error`:
  
<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/a109c6f2-023a-45c8-a0a7-7573138b546d"> 

- The associated DRC error will be displayed in the tkcon window
- For more information on DRC errors plase refer to: https://skywater-pdk--136.org.readthedocs.build/en/136/
For more information on how to fix these DRC errors using Magic please refer to: http://opencircuitdesign.com/magic/

## PEX Extraction with Magic
- To extract the parasitic spice file for the associated layout one needs to create an extraction file
- After generating the extracted file we need to output the .ext file to a spice file

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/c250d9a3-d9aa-4c0a-97b4-b97f21191196"> 

- What's inside spice file that is created ???
- `vim sky130_inv.spice`

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f5dcfd77-c96f-4ab9-99ff-36bee95db4d1"> 

 - Umm... Not much !!!
- Has intervert netlist details
- Modify the file wrt requirement
    - Grid size from the layout is 0.01u
    - specify the library for MOS
    - create VDD, VSS, Input pulse Va
    - specify the type of analysis to be done
      
 - **GRID size** 

<img width="550" alt="image" src="https://github.com/vandhana01/pes_openlane_pd/assets/142392052/61b23c2e-2de9-46ad-b3f9-254e6a3d1550"> 

## Modified Spice netlist

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/83eee9a8-fbca-4992-8113-d7075421d135)
 

- To run the simulation with ngspice, invoke the ngspice tool with the spice file as input
- `nyspice sky130_inv.spice`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/6edc6cba-af2b-47ee-9569-4bd0657dfd12)

- Graph
- `plot y vs time a`
   
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/51425c06-4f15-4d1b-9b85-97fe9f1bb2f3)


 - Characterise the cell
   1. **Rise Transition** : 0.0395ns (the transition of a signal from a low (logic 0) to a high (logic 1) voltage level)
   2. **Fall transition** : 0.0282ns (  the transition of a signal from a high (logic 1) to a low (logic 0) voltage level)
   3. **Cell Rise delay** : 0.03598ns ( the time it takes for the output of a logic cell or gate to make a valid transition from a low to high voltage level (i.e., a rise transition) in response to a change in its input)
   4. **Cell fall delay** : 0.0483ns (the time it takes for the output of a logic cell or gate to make a valid transition from a high to low voltage level (i.e., a fall transition) in response to a change in its input)
</details>

## DAY 4
<details>
<summary> Pre-layout timing analysis and importance of good clock tree </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)


# Timing modelling using delay tables
- Using an abstract view of the GDS files generated by Magic, Place and routing (PnR) is performed . The abstract information will include metal and pin information. The PnR tool will use the abstract view information, formally defined as LEF information, to perform interconnect routing in conjunction to routing guides generated from the PnR flow.
  
## An Introduction to LEF Files
- Technology LEF : Contains layer information, via information, and restricted DRC rules
- Cell LEF : Abstract information of standard cells


## Extraction of LEF
- guidelines to get standard cell set
   - Input and output ports must lie on the intersection of vertical and horizontal tracks
   - Width of the standard cell should be odd multiples of the track pitch and height should be odd multiple of vertical track pitch
- `Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/57f600e7-02a5-446c-a66b-3c17ba7938d0)


## Standard Cell Pin Placement


- To display the grid in magic:
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/66cfc396-0c3c-4148-8873-489823d66084)

- Viewing the grid we can ensure our pin placement is optimized for PnR flow:

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/fc6ea8f8-c399-4c81-830a-f5f573930c0a)

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/2602f008-4696-487f-9950-965cd4a5320e)

## LEF Generation in Magic
- Magic allows users to generate cell LEF information directly from the Magic terminal.
- To generate the cell LEF file from Magic perform:
1. First  `save sky130_vsdinv.mag` and `exit` from new grid from console
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/2d64fb7b-ad0f-4137-a3c8-70dfc1246748)


2. Then open the file and extract LEF 
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/0e63643d-c976-4d6a-b94c-91e703ae8271)

- **Generated cell LEF file**:
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/92d2570f-e78b-4db6-81ce-c8ddb453388d)

  
## Including Custom Cells in OpenLANE
- In order to include the new cells in OpenLANE we need to do some initial configuration:
  1. Fully characterize new cell with GUNA for specified corners
  2. Include cell level liberty file in top level liberty file
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/2a5de7a7-3b55-437c-bcab-187495a17133)


  3. Reconfigure synthesis switches in the `config.tcl` file
     
- we need the lef file, library file that has cells
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/a8baef98-a854-4663-bab2-65267ac88b41)

  - Change config file so that these libraries and lef file is used
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/fdc98308-e976-4081-804a-85b987c033bb)


- Note: This step will also include any extra LEF files generated for the custom standard cell(s)
Overwrite previous run to include new configuration switches

   4. Overwrite previous run to include new configuration switches
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/10e0d8c9-6a26-49c8-b088-236412e9c59e)

     
   5. Add additional statements to include extra cell LEFs
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/e38648be-a183-4daf-9f31-b2dd8eae3dbf)


- Check synthesis logs to ensure cell has been integrated correctly
  - `run_synthesis`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/44c3a374-210d-4ad5-8ad3-cd735639d768)

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/78b3ed52-bc25-49fe-88db-58e625649cd8)

- vsdinv cell has been used in synthesis process!!
-  floorplan and placement : `init_floorplan`  `run_placement`
-  to view the design we type the command
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/4cecba55-316a-4356-a483-b05a6f65b71b)


- LAYOUT
  
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/bf5afaad-c506-411e-83a7-07987fcf70ca)

- Zoom in by clicking `z` in keyboard and `v` to fit screen
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/feaec9b1-f026-48a6-a858-9b1a2882287e)


# Timing Analysis with Ideal Clocks using OpenSTA
  
# Fixing Slack Violations
VLSI engineers will obtain system specifications in the architecture design phase. These specifications will determine a required frequency of operation. To analyze a circuit's timing performance designers will use static timing analysis tools (STA). When referring to pre clock tree synthesis STA analysis we are mainly concerned with setup timing in regards to a launch clock. STA will report problems such as worst negative slack (WNS) and total negative slack (TNS). These refer to the worst path delay and total path delay in regards to our setup timing restraint. Fixing slack violations can be debugged through performing STA analysis with OpenSTA, which is integrated in the OpenLANE tool. To describe these constraints to tools such as In order to ensure correct operation of these tools two steps must be taken
   1. Design configuration files (.conf) - Tool configuration files for the specified design
   2. Design Synopsys design constraint (.sdc) files - Industry standard constraints file
- For the design to be complete, the worst negative slack needs to be above or equal to 0. If the slack is outside of this range we can do one of multiple things
  1. Review our synthesis strategy in OpenLANE
  2. Enable cell buffering
  3. Perform manual cell replacement on our WNS path with the OpenSTA tool
  4. Optimize the fanout value with OpenLANE tool

## Cell Fanout Example:

- We must create two files
   - first one must be in the openlane directory, known as the 'pre_sta.conf' file
   - The second is the my_base.sdc file
- To run the timing analysis : `sta pre_sta.conf`
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/0cbe7b2c-2bbc-43bb-b518-a49e76d0d3f4)

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/3c281485-2eaa-4dd4-b147-f2072c6366e8)


- `set ::env(SYNTH_MAx_FANOUT) 4`  reduces the slack violation
- The delay of this cell is large due to a high load capacitance due to high fanout. To fix this problem we can re-run synthesis within OpenLANE after reconfiguring the maximum fanout load value.

## Cell Replacement Example
- To determine what loads our net is driving in OpenSTA we can report net connecitons
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/582bfa26-3fef-4703-8642-8ab2c3369edf)


## Clock Tree Synthesis
- After running floorplan and standard cell placement in OpenLANE we are ready to insert our clock tree for sequential elements in our design. Two of the main concerns with generation of the clock tree are:
1. Clock skew - Difference in arrival times of the clock for sequential elements across the design
2. Delta delay - Skew introduced through capacitive coupling of the clock tree nets
- we write this netlist using `write_verilog` and replace the openlane generated mapped file ie., `picorv32a.synthesis.v`
- openlane flow: ` run_flooorplan`  `run_placement`  `run_cts`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/bfaa26fc-07ad-472f-9ede-4ab6b0439347)


- Note: To ensure timing constraints CTS will add buffers throughout the clock tree which will modify our netlist

# Post CTS- STA Analysis
- OpenLANE has the OpenROAD application integrated into its flow. The OpenROAD application has OpenSTA integrated into its flow. Therefore, we can perform STA analysis from within OpenLANE by invoking OpenROAD.
- In OpenROAD the timing analysis is done by creating a .db database file. This database file is created from the post-cts LEF and DEF files. To generate the .db files within OpenROAD
## Timing Analysis with Real CLocks using OpenSTA
- Type the command `openroad` first
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/52c8e869-5dd9-49c5-8016-c4801fb11539)


- read the .lef file : `read_lef /openLANE_flow/designs/picorv32a/runs/17-09_09-08/tmp/merged.lef`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/88b01b4a-6809-455f-98c1-13de02efe076)

- read the .def file: `read_def /openLANE_flow/designs/picorv32a/runs/17-09_09-08/results/cts/picorv32a.cts.def`

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/1f3ac3dd-6460-4e5a-aeae-4241c3ee5e87)


```c
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/17-09_09-08/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(LIB_SLOWEST)
read_liberty -max $::env(LIB_FASTEST)
```
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/08bd038b-3cf6-49c5-92a5-6be536a908a8)


- read the src file : `read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc`
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/3adbd09e-a207-48f1-bd57-97b8e200b918)

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/69bb61e1-b106-456c-8ea9-390fdc8faebd)


- We set the clock and Checking the report
- Perform it again for a more accurate result
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/f224eea0-09e7-4b99-b8ba-407323de91c2)


![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/9258275a-4a9e-4ac6-bce4-fedab922ab07)


- then `report_clock_skew -hold` and `report clock_skew -setup`
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/61bb17bd-1f08-43f3-974f-dddeb78ccfed)

  
- Note: Whenever the DEF file changes we need to recreate this .db file

</details>

## DAY 5
<details>
<summary> Final steps for RTL2GDS using tritonRoute and openSTA </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)

# Power Distribution Network Generation
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/c56fdc35-1bce-481e-8d4d-99f74c5bfbb4)

- To generate the PDN in OpenLANE :`gen_pdn`
![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/5325819c-1127-43a4-a9ee-30aa8504292f)

The PDN feature within OpenLANE will create:
1. Power ring global to the entire core
2. Power halo local to any preplaced cells
3. Power straps to bring power into the center of the chip
4. Power rails for the standard cells

![image](https://github.com/vandhana01/pes_openlane_pd/assets/142392052/5f195586-fa4d-4d18-bbbc-036c13b915fc)


# Global and Detailed Routing
- OpenLANE uses TritonRoute as the routing engine for physical implementations of designs. Routing consists of two stages
1. Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed
2. Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides

- If DRC errors persist after routing the user has two options:
1. Re-run routing with higher QoR settings
2. Manually fix DRC errors specific in tritonRoute.drc file

## SPEF Extraction
- After routing has been completed interconnect parasitics can be extracted to perform sign-off post-route STA analysis. The parasitics are extracted into a SPEF file. The SPEF extractor is not included within OpenLANE as of now.
- `cd ~/Desktop/work/tools/SPEFEXTRACTOR
python3 main.py <path to merged.lef in tmp> <path to def in routing>`
  
</details>
