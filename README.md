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

<img width="350" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/03b887a4-97b7-4139-8bc9-e7c725d3bea6">
-->

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/c52d516e-1f09-4ea7-953a-f72482f09beb">

- QFN-48(Quad Flat No-Lead 48) package is a commonly used IC packaging format known for its compact size and thermal efficiency.
- Within this package, several crucial components play distinct roles in the functioning of an electronic device:
  
- **QFN-48 Package**
   - The QFN-48 package refers to the physical housing that encases an integrated circuit.
   - It features a flat, square or rectangular shape with a set number of external pins or leads for electrical connections.
   - The "48" in QFN-48 indicates the total number of pins on the package.
<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/625b8397-5bb4-42ef-829c-1844e51ac5e0">

- **Chip**
   - The chip, also referred to as the integrated circuit (IC) or die, represents the heart and brains of the electronic device.
   - This tiny silicon wafer contains intricate semiconductor components, including transistors, resistors, and capacitors, arranged to execute specific functions as per the device's design and intended application.
   - The chip is encapsulated within the QFN-48 package.
<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/bcdf7650-66a1-49c5-9fa8-19e86e3cd7d6">

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

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/8b8087f2-bf2f-4325-9a1d-43540158cd39">

- **IPs**
   - Intellectual properties (IPs) are modular components that can be integrated into the chip's design to add specific functions, making the overall design process more efficient and cost-effective.
   - **Foundries** play a crucial role in the semiconductor industry by providing semiconductor manufacturing services to companies that design ICs but do not have the facilities or expertise to produce them in-house.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/b6029bd0-f1f9-44db-a5e0-c8a65d7c3ec3">

## Introduction to RISC-V
- The RISC-V Instruction Set Architecture (ISA) is an open and royalty-free standard ISA for designing efficient and scalable computer architectures.
- Open Standard: RISC-V is an open and royalty-free ISA managed by a consortium, allowing anyone to implement it without licensing fees.
- Modular Design: It offers different instruction sets and optional extensions for diverse applications, promoting flexibility.
- Simplified ISA: Following the RISC philosophy, it features a streamlined and orthogonal instruction set for efficient hardware design and compiler optimization.
- Scalability: RISC-V scales from small embedded devices to high-performance systems with 32-bit, 64-bit, and 128-bit address spaces.

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/b63793d6-c597-49b0-aebd-13f3ff3a95af">

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

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/5b616cf7-4ac8-414d-9574-b157b1576cc8">

# SoC design and OpenLANE 


## Introduction to all components of open-source digital asic design
The open-source approach aims to democratize and make ASIC design more accessible to a broader community of engineers and designers, fostering innovation and collaboration.

<img width="562" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/1171e642-7326-42c1-bca2-a6c010cd2cf6">


## Simplified RTL2GDS flow
Register Transfer Level to Graphic Data System flow is a complex and multi-step process used to design and fabricate integrated circuits (ICs).

- **RTL (Register Transfer Level)**:
   - RTL is a level of abstraction in digital circuit design that represents the functionality and behavior of a digital system. It describes how data flows through registers and how logical operations are performed within a digital circuit.Designers create RTL descriptions using hardware description languages (HDLs) like VHDL or Verilog.
- **GDS (Graphics Database System)**:
   - GDS is a file format and a set of tools used for representing and manipulating the physical layout of integrated circuits. GDS files contain information about the position, shape, size, and connectivity of all the components and interconnects on a semiconductor chip.   

<img width="563" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/e8b3fb18-d79b-4f1a-a8bf-7b0defb2b226">

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
     
![image](https://github.com/vandhana01/pes_pd/assets/142392052/3ac775c1-b3b8-4550-b639-0b2fa1ef47cc)

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
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/32118d3a-528e-488f-8e7a-b02668ce8159)
  
- OpenLANE is an open-source EDA toolchain that aids in the design and verification of digital chips, while Strive Chipsets are the customized semiconductor chipsets created using EDA tools like OpenLANE to address specific application or market needs. Together, they represent the intersection of open-source collaboration and customized semiconductor design for a wide range of industries and applications.

![image](https://github.com/vandhana01/pes_pd/assets/142392052/b6d8ee77-0a50-408e-8f61-9547f3186796)


# Get familiar to open-source EDA tools
## Skywater PDK Files
![image](https://github.com/vandhana01/pes_pd/assets/142392052/bb09b40b-81e2-413e-b035-110056d1992b)

- There are three subdirectories
   - **Skywater-pdk**: Contains all the PDK related files
   - **Open_pdks**: Contains scripts that are used to bridge the gap between closed-source and open-source PDK to EDA tool compatibility
   - **Sky130A**: Compatible open-source PDK files
## Invoking OpenLANE
![image](https://github.com/vandhana01/pes_pd/assets/142392052/bebf9028-f10d-4d81-b6ea-98c5f4ea3174)

- `flow.tcl` is the file that contains the script to run the designs
- `-interactive` - runs step by step process (interactive mode)
## Importing package
![image](https://github.com/vandhana01/pes_pd/assets/142392052/9adf9b64-36eb-4e5f-92e7-d08ee52a5365)


- `package require openlane 0.9` To import all the packages that are required to run OpenLANE
## OpenLANE design folder
![image](https://github.com/vandhana01/pes_pd/assets/142392052/fd358940-646d-4122-97b4-9a5b5d73b8e9)


- All the designs run within OpenLANE are in design folder
## Hierarchy of Design folder
![image](https://github.com/vandhana01/pes_pd/assets/142392052/d1904b49-8d5b-48af-92de-42e287815288)


Every design folder has_
- `Src folder` : Contains verilog files and sdc constraint files
- `Config.tcl files`: Design specific configuration switches used by OpenLANE
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/ba91f191-1070-431f-ab38-4daa55950a8b)
  -`less config.tcl` 
## Prepare the design
- To Setup files specific to the design flow
- `prep -design <design_name>`
![image](https://github.com/vandhana01/pes_pd/assets/142392052/e5c6b465-9190-4532-af78-266eae5a4366)

- After design prep , there will be a new run directory created ,where all the results will be stored. 
![image](https://github.com/vandhana01/pes_pd/assets/142392052/42572d0b-1db4-4c65-bfd2-f20c2cad3859)

 ## Synthesis
![image](https://github.com/vandhana01/pes_pd/assets/142392052/4f0a7927-c389-4a6d-a71f-f6ad5507dd1d)

- `run_synthesis`: To run synthesis
- After synthesis find the flop ration = No. of D flip flops / Total number of cells
![image](https://github.com/vandhana01/pes_pd/assets/142392052/7986d27b-900e-4cab-b0fa-98c58cff6e90)

 
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

![image](https://github.com/vandhana01/pes_pd/assets/142392052/2d27055e-b8e8-439f-88a6-4b32779c75b8)


 - floorplanning will be run according to configuration settings in the design specific `config.tcl` file.
![image](https://github.com/vandhana01/pes_pd/assets/142392052/ce744385-d657-4dec-9a43-629029eb5981)
 - `run_floor` in openlane to execute the floorplanning step.
 - an essential command in OpenLANE for creating the initial physical floorplan of an ASIC design. 
![image](https://github.com/vandhana01/pes_pd/assets/142392052/03788a05-ebe5-4e1c-8458-09fe31893b44)

 - Output is the `def` file  (design exchange format)
 - contains important information about the physical layout of the chip, including the positions and dimensions of cells, placement of I/O pads, the power grid structure, and other physical design details.
 
- `less picorv32a.floorplan.def`

![image](https://github.com/vandhana01/pes_pd/assets/142392052/b63baf1f-f822-47e1-97d3-db4fa2b2170e)

7. **Floorplan layout in Magic**
  - To see actual layout after floorplan
  - `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &`
  -  setting up the "magic" tool for the specified technology node, reading in a LEF file describing a standard cell library, and reading in a DEF file that likely contains the floorplan for an IC design based on the Picorv32 processor core.
  -  The "&" symbol at the end of the command allows you to run multiple commands in a single line
  
<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/d52c032c-07ce-420d-9d55-22493e1567da">  


# Library Binding and placement
-  They involve selecting and placing standard cells from a library onto the chip's floorplan. They provide the foundation for subsequent stages in the ASIC design flow, including routing, verification, and manufacturing preparation.
1. **Netlist binding and initial place design**
   - Library will have width and height of cells, delay/timing info, required conditions, various shapes gates, various flavours of cells, etc
   - Netlist binding, also known as cell binding or logic binding, is the process of associating logical functions or gates from a high-level RTL (Register-Transfer Level) design with specific standard cells or library cells from a cell library.
   - The primary goal of initial placement is to create a starting point for the detailed placement step. It provides a rough layout of cells on the chip, ensuring that critical paths are appropriately positioned and that power and clock distribution networks can be efficiently established.
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/257c82b0-d23c-439b-975e-b9bc6daeab93">     


2. **Optimize placement**
   - Clearly define your optimization objectives, which may include minimizing wirelength, meeting timing constraints, optimizing for power distribution, and achieving area efficiency.
   - This is the stage where we estimate wire length and capacitance and based on that, insert repeaters(buffers that recondition the original signal and make a new signal and send it to following stage to maintain signal interigty)
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/3fe951b0-7941-452b-8954-6a6875737d1e">

   - timing analysis is done, assuming that all the clock signals are performing at ideal rate , to check wheather the placement done reasonable or not
    
3. **Placement**
- **Global Placement**: Initially, use global placement algorithms to provide a rough placement of cells. These algorithms consider high-level objectives and balance different goals. But not a legal placement
- **Detailed Placement**: Detailed placement refines the positions of individual cells, optimizing for local objectives, Legalize the cell placement, addressing timing and congestion issues.

  - `run_placement` : Global placement is performed
- `cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs`
- after `ls` follow up with `<data>` `results` `placement` `picorv32a.placement.def`
- `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &`
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/7ca97c32-2c15-411e-8ff1-abd3d599c744"> 
Zoom in
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/4a1ed8ed-13fc-4b5b-9701-04acec3195bf">

# Standard Cell design and characterization flow
- They are pre-designed and pre-characterized logic gates or functional blocks with fixed heights that are used to implement digital logic functions in an IC. 
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/ef79f06b-c292-4bc7-8587-a7a2f03a7b87">

- **Cell Design Flow** ___
  1. Inputs : Process design kits(PDKs), DRC & LVS rules, SPICE models, library and user-defined specs.
  2. Design Steps : Circuit Design, Layout Design, Characterization. The software GUNA used for characterization. The characterization can be classified as Timing characterization, Power characterization and Noise characterization.
  3. Outputs : CDL (Circuit Description Language), GDSII, LEF, extracted Spice netlist (.cir), timing, noise, power.libs, function.
     
- **Characterization flow**
    - These libraries, along with their associated Liberty files, play a key role in enabling synthesis tools to determine the optimal arrangement of standard cells in an IC design.
      
<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/5a2ec424-d8d3-4e0a-99b7-837f4aec1c6e">   

<img width="450" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/3a5a7e3e-e98b-4cb1-a4b6-8bde6d58b920"> 

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
<img width="500" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/879552d0-0a6d-4bc5-8632-8e5d391772c6">
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

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/14638358-bba0-46ad-b767-5cb2691c910e"> 

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
<img width="500" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/e04baa88-ad44-463f-9443-d9d37fb7fc9c">
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
<img width="500" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/707695d7-35ed-430d-aaf9-b017aae33cac">
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

![image](https://github.com/vandhana01/pes_pd/assets/142392052/5a104049-efbe-4ca8-9d07-052d85395304)

# Sky130 Tech File Labs

## Magic Layout View of Inverter Standard Cell         
- Git clone : `https://github.com/nickson-jose/vsdstdcelldesign` for cell files
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/e67be7bb-47c7-4dc4-82e6-9accf5f1b385)
 

![image](https://github.com/vandhana01/pes_pd/assets/142392052/556532f6-72f3-41a1-84ee-0169ff43ea51)


-  `cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag &`

<p align="center">
<img width="300" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/15decefe-627b-47f4-b869-4f53abe0952a">
</p>

- Magic Key Features:
   1. Color Palette - Defines layers and associated colors
   Continuous DRC
   2. Device Inference - Automatic recognition of NMOS and PMOS devices
      
- **Device Inference** :
- Select the specific layer/device by hovering over the object and pressing, s, iteratively, until you traverse the hierarchy to the specified object
- move the cursor to a required area, and press `s`
- Run the what command in the tkcon window:

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/0065c736-5da8-4576-9f15-e093c2f09bce"> 

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

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/f7f0de0c-41c2-4c79-a27c-1d1d5ca3255f"> 

- What's inside spice file that is created ???
- `vim sky130_inv.spice`

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/d020d2fe-8451-462d-be5e-a09cf2516d5d"> 

 - Umm... Not much !!!
- Has intervert netlist details
- Modify the file wrt requirement
    - Grid size from the layout is 0.01u
    - specify the library for MOS
    - create VDD, VSS, Input pulse Va
    - specify the type of analysis to be done
      
 - **GRID size** 

<img width="550" alt="image" src="https://github.com/vandhana01/pes_pd/assets/142392052/757a8b90-8f38-4b80-9022-8cbcb2f9edef"> 

## Modified Spice netlist

![image](https://github.com/vandhana01/pes_pd/assets/142392052/aa5ed965-00aa-4647-8550-f2f6143e2cdb)
 

- To run the simulation with ngspice, invoke the ngspice tool with the spice file as input
- `nyspice sky130_inv.spice`
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/dbe2cffa-c4e4-41b6-a227-3ec42e98acf6)

- Graph
- `plot y vs time a`
   
![image](https://github.com/vandhana01/pes_pd/assets/142392052/475114b5-714f-4455-9573-f17415bf619e)


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

![image](https://github.com/vandhana01/pes_pd/assets/142392052/ea84d361-b6c8-472b-b8dd-3b9e96aa0611)


## Standard Cell Pin Placement


- To display the grid in magic:
![image](https://github.com/vandhana01/pes_pd/assets/142392052/f19366f0-5f6f-456d-b995-fa353d807b56)


- Viewing the grid we can ensure our pin placement is optimized for PnR flow:

![image](https://github.com/vandhana01/pes_pd/assets/142392052/d4bc00de-a2c4-4d0e-8b2a-d160556f6b50)

![image](https://github.com/vandhana01/pes_pd/assets/142392052/8beec9fb-5f0f-48f5-8909-f58917ebe287)

## LEF Generation in Magic
- Magic allows users to generate cell LEF information directly from the Magic terminal.
- To generate the cell LEF file from Magic perform:
1. First  `save sky130_vsdinv.mag` and `exit` from new grid from console
![image](https://github.com/vandhana01/pes_pd/assets/142392052/0f0bb0c7-338a-408b-8002-3f053412001e)

2. Then open the file and extract LEF 
![image](https://github.com/vandhana01/pes_pd/assets/142392052/056ce031-ba6b-4d3d-b98f-164fa943f24a)

- **Generated cell LEF file**:
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/18447044-9765-40df-bd94-1ab1d3500137)
  
## Including Custom Cells in OpenLANE
- In order to include the new cells in OpenLANE we need to do some initial configuration:
  1. Fully characterize new cell with GUNA for specified corners
  2. Include cell level liberty file in top level liberty file
 ![image](https://github.com/vandhana01/pes_pd/assets/142392052/e7a52951-b47e-4829-8bd6-b67d713446f3)

  3. Reconfigure synthesis switches in the `config.tcl` file
     
- we need the lef file, library file that has cells
  
![image](https://github.com/vandhana01/pes_pd/assets/142392052/e6ce022e-5a1e-48e6-95fa-f08ba1a5d7da)

  - Change config file so that these libraries and lef file is used
![image](https://github.com/vandhana01/pes_pd/assets/142392052/1ce70d96-34bb-4b3c-917e-b369548a4109)

- Note: This step will also include any extra LEF files generated for the custom standard cell(s)
Overwrite previous run to include new configuration switches

   4. Overwrite previous run to include new configuration switches
![image](https://github.com/vandhana01/pes_pd/assets/142392052/8bdfe1eb-f227-4f70-9288-bfcd05b18990)
     
   5. Add additional statements to include extra cell LEFs
![image](https://github.com/vandhana01/pes_pd/assets/142392052/8ebad0c0-dc9d-4e96-9566-647e49463c77)

- Check synthesis logs to ensure cell has been integrated correctly
  - `run_synthesis`

![image](https://github.com/vandhana01/pes_pd/assets/142392052/76aa141b-cd49-4e74-bb84-6c20b88d027b)


![image](https://github.com/vandhana01/pes_pd/assets/142392052/49c15fbd-2c84-4b51-98a5-cefd30e1feef)

- vsdinv cell has been used in synthesis process!!
-  floorplan and placement : `init_floorplan`  `run_placement`
-  to view the design we type the command
![image](https://github.com/vandhana01/pes_pd/assets/142392052/3b2d5afc-1152-4f21-991b-83f9d7b48f51)

- LAYOUT
  
 ![image](https://github.com/vandhana01/pes_pd/assets/142392052/bfee562e-fc2c-4a58-b6af-91f2849121a6)

- Zoom in by clicking `z` in keyboard and `v` to fit screen
![image](https://github.com/vandhana01/pes_pd/assets/142392052/2d4a0163-7012-468a-a7ef-bd8240d49e08)

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
-To run the timing analysis : `sta pre_sta.conf`
![image](https://github.com/vandhana01/pes_pd/assets/142392052/29798695-c441-4600-bf33-8bd665db7537)

![image](https://github.com/vandhana01/pes_pd/assets/142392052/f3a3f0d6-4d5d-42fd-9ce7-8c185728b51c)

- `set ::env(SYNTH_MAx_FANOUT) 4`  reduces the slack violation
- The delay of this cell is large due to a high load capacitance due to high fanout. To fix this problem we can re-run synthesis within OpenLANE after reconfiguring the maximum fanout load value.

## Cell Replacement Example
- To determine what loads our net is driving in OpenSTA we can report net connecitons
![image](https://github.com/vandhana01/pes_pd/assets/142392052/a6f55ca0-ea60-4354-a860-a98130337d85)

## Clock Tree Synthesis
- After running floorplan and standard cell placement in OpenLANE we are ready to insert our clock tree for sequential elements in our design. Two of the main concerns with generation of the clock tree are:
1. Clock skew - Difference in arrival times of the clock for sequential elements across the design
2. Delta delay - Skew introduced through capacitive coupling of the clock tree nets
- we write this netlist using `write_verilog` and replace the openlane generated mapped file ie., `picorv32a.synthesis.v`
- openlane flow: ` run_flooorplan`  `run_placement`  `run_cts`

![image](https://github.com/vandhana01/pes_pd/assets/142392052/f0ae4817-8792-4e95-b810-1db1213e11b5)


- Note: To ensure timing constraints CTS will add buffers throughout the clock tree which will modify our netlist

# Post CTS- STA Analysis
- OpenLANE has the OpenROAD application integrated into its flow. The OpenROAD application has OpenSTA integrated into its flow. Therefore, we can perform STA analysis from within OpenLANE by invoking OpenROAD.
- In OpenROAD the timing analysis is done by creating a .db database file. This database file is created from the post-cts LEF and DEF files. To generate the .db files within OpenROAD
## Timing Analysis with Real CLocks using OpenSTA
- Type the command `openroad` first
![image](https://github.com/vandhana01/pes_pd/assets/142392052/d6c7bb4c-19cc-44d6-9598-12d6590dfdb9)

- read the .lef file : `read_lef /openLANE_flow/designs/picorv32a/runs/17-09_09-08/tmp/merged.lef`

![image](https://github.com/vandhana01/pes_pd/assets/142392052/7fde30cf-5f2e-4849-977b-caeae491954e)

- read the .def file: `read_def /openLANE_flow/designs/picorv32a/runs/17-09_09-08/results/cts/picorv32a.cts.def`

![image](https://github.com/vandhana01/pes_pd/assets/142392052/e1d880ca-9fd0-4691-b306-c817b82b4422)

```c
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/17-09_09-08/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(LIB_SLOWEST)
read_liberty -max $::env(LIB_FASTEST)
```
![image](https://github.com/vandhana01/pes_pd/assets/142392052/bd56f415-4664-4568-996b-011049b7d5d8)

- read the src file : `read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc`
 ![image](https://github.com/vandhana01/pes_pd/assets/142392052/6577d19d-587d-40f3-af1f-3bb5dd2781a8)

![image](https://github.com/vandhana01/pes_pd/assets/142392052/12a40982-a18c-4c2d-99bf-a7dfa63a3ce3)

- We set the clock and Checking the report
- Perform it again for a more accurate result
![image](https://github.com/vandhana01/pes_pd/assets/142392052/92465873-eff6-4857-b6f8-006a7abe7883)

![image](https://github.com/vandhana01/pes_pd/assets/142392052/c5c989ea-2f39-41fa-b814-481bd2ac79ce)

- then `report_clock_skew -hold` and `report clock_skew -setup`
![image](https://github.com/vandhana01/pes_pd/assets/142392052/986d0180-3228-4516-82c4-ecabd90394f7)

  
- Note: Whenever the DEF file changes we need to recreate this .db file

</details>

## DAY 5
<details>
<summary> Final steps for RTL2GDS using tritonRoute and openSTA </summary>
<br>
  
[](https://github.com/vandhana01/pes_asic_class#links-for-easy-navigaton)

# Power Distribution Network Generation
![image](https://github.com/vandhana01/pes_pd/assets/142392052/9c49bebd-8dd8-484b-a43c-ccdc249b51c2)


- To generate the PDN in OpenLANE :`gen_pdn`
![image](https://github.com/vandhana01/pes_pd/assets/142392052/aa6d8fb0-51ae-4622-8848-2ae6ea09d5ce)

The PDN feature within OpenLANE will create:
1. Power ring global to the entire core
2. Power halo local to any preplaced cells
3. Power straps to bring power into the center of the chip
4. Power rails for the standard cells

![image](https://github.com/vandhana01/pes_pd/assets/142392052/0196b2ab-4f96-4a79-8b27-293e74c4e9c4)

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
