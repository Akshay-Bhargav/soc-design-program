# soc-design-program
## DAY 1
### How to talk to computers
#### Introduction to QFN-48 PAckage,Chip,Pads,core,die and IPs
##### Arduino Leonardo:
  Basically Ardunio Boards are the microcontroller platform which gives easy of communication between the hardware and the softwre. We can easily do the hardware comnections and can easily code the necessary code for the projects. Arduino Leonardo is one of the type of hardware-software platform which is based in on the ATmega32u4. This board inculdes 20 digital I/O pins and a crystall oscillator of 16MHz frequency. In the 20 I/O ports 12 pins work as analog inputs and 7 pins are Pulse width modulation outputs.It also includes a USB connection, a power jack, reset pin and the ICSP header.It can be switch on with the help of the adaptor and also by connceting it to the computer through USB cable. ![arduino-leonardo-board1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/14ffae04-199f-42d1-9a83-454208820a4a)

  Our objective of this course mainly deals with the chips or the processor as mentioned with the square box in the above picture.
Processors are the brain of the system which carry outs the programs,computes data, and coordinates the activity of other system components.It cannot work alone so it will be integrated with many more devices.
  
##### Peripherals of the chip/processor :
  Across the chip/processor we will be able to see many more interface conncetion across the board as show in the below picture![processor](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/80568241-de26-4f3e-b6de-22bfa06ff785)

  Processor has been connected to many more interfaces such as to the JTAG UART which helps in the communication between the external devices without the mediating devices such as RS-232.Also it will be connceted to the SDRAM for the Memory,Flash,Voltage connection,Ground,ADC etc.

##### Packages : IC Packages protect the semiconductor devices and components and helps in the integration of the IC with the electronic devices. There are different types of packages such as:
* Through hole Packages: It is the type of package where 1 or more leads go through holes of PCB and gets connected using the solder.The other types in this are
    - SIP(Single In Line Package)
    - DIP(Double In Line Package)
    - PGA(Pin Grid Array)
      
* Surface Mount Packages: This is the Package where the external devices are mounted on the PCB board.The most common technique used in this type are
     - QFN(Quad Flat No-Lead):These are compact sized,the model QFN-48 has 48 pins in it where the chip will be having pins in all the 4 sides.In the below figure we can see the QFN-48 packaged chip![pp](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ff015b50-e362-46cd-832e-5575ae7b8cab)
     - Ball Grid Array : Instead of leads in this we use metall balls to create the respective connection
       
* Contact Less Packages: In this type there will be no physical connection between the PCM.

Inside the chip there is a Square Patch which has been divided into many regions as shown in the figure![fo](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0a1e9cc7-07c5-4c7d-93ad-daba667dd01f)

##### Core : Area inside the chip where all the digital logic takes places with the help of the digital ciruits with in it.
* Pads : Pads are the medium through wich the input and output signals has to pass.
*  Die : Small block of semiconducting materials on which the Pads has been built and mainly refers to the cornors of Square patch.
*   Foundry IP's : Foundry will helps in providing the essential building block for the chip design,allowing the designer to leverage pre-designed components optimized for specific purpose technologies.
  
#### Intro to RISC-V
RISC refers to the Reduced Instruction Set Computer where V stands for the fifth generation of the architecture.The instructions given will be less and the instuctions will be simple.It consists of more number of general purpose registers. The RISC-V architecture provides the benifit of pipelining.The addressing modes are simple. RISC-V is a open source insturction set architeture which allows the user to customize .It takes single clock cycle for the execution of the instruction.The base instruction set has a fixwd length of 32-bits and the ISA supports variable length extensions where each instruction can be any number of 16 bit parcels in length.The memory usuage of the RISC will be high and also the price of the chip will be costlier than the CISC.

####  From Software Applications to Hardware
This section deal with how the signals are read by the RISC-V

When we run the application the commands  will get read through the System Software and then it will get passed through the Hardware.
![l1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d702a8c2-661a-4867-9c61-85edb369d6ed)

##### System Software:
 The flow of the insturction in the System Software can be divided into 3 parts such as:
  * Operating system:
    OS handles the I/O operations and place a crucial role in allotment of memory.It will be having all the details regarding the I/O pins configurations,buses,Interrupts etc. It will conduct low level system functions
  
  * Compiler :
   The inputs will be in a standard form and the user will do the necessary code or build the inputs in the high level language such as C,C++,Java,Python,HTML.When these inputs comes to the compiler it will convert the high level language into assembly level language.This output from the compiler is termed as the Instuction sets which will be in the .*exe file format and will be in hexa-decimal for RISC-V.The compiler will convert the inputs into the instruction set based on the respective forms of hardware.Instruction sets will act like a interface or bridge between the code and the hardware and thus it is called as Abstruct Interface.The hardware is dependent on these instruction sets so it is called as the architecture of the computer.
  ![abst](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2ef3e745-f669-49a8-b62a-12182ab13445)

  * Assembler :
   Assembler takes the instruction set which will be there in the assembly level language and converts it into the binary format or the machine level language which can be understood by the hardware. As per the output of the assembler the harware will generate the chip layout. The output of the assembler will be in binary form.

##### Hardware:
   Hardware Description Language ensures the conversion of instuctions sets into the binary format or to RTL language. Then after the instuction getting into the RTL format it will generate a netlist which includes the connection of the logic gates. Basically netlist helps in the gate level description of the code. AS per the netlist design the physical design gets implemented or the layouts will be built inside the chip.
  
##### Code flow can be divided into 3 parts:
  * RISC-V ISA (till the generation of ISA).
  * RTL and Syntehsis of RISC-V based CPU core(till netlist generation).
  * Physical Design Implementation.
![3a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/acf0c6cf-3d3a-4e9b-a961-af4a97f32c3b)

### Soc Design and OpenLANE

#### Introduction to all components of open-source digital asic design
ASICs refers to the Application Specific Integrated Ciruits which means the IC is designed too carry out only a specific function. Unlike the general purpose ICs which can be optimized to do many works ASICs are customized for a single set of work.
Elements required for desiging  ASIC are:
* RTL IP's(Register-Transfer Language):It consits of the HDL RTL models of the function which we want to implement  also it contains the netlist of the chip. Mainy open soruce RTL Design tools are available such as librecores.org, opencores.org, github.com
* EDA Tools(Electronic Design Tools):These arre the CAD tools for EDA which will help us in the layout design and geometry of the layout.Many open source EDA tools are available such as QFlow,OpenRoad, OpenLANE, Spice simulator, SIC, Magic etc.
* PDK DATA(Process Design Kit):In the past the design and fabrication was done simultaneously but in 1979 Lynn Conway and Carver separated the design and fabrication process by implementing Lambda based Design Rules.So now PDK files are the interface between FAB and the designers.PDK will have information regarding the I/O libraries, design rules Digital standard cell libraries, device models etc.Presently the open source for the PDK files is the combination of Google and SKywater 130nm Technology.![distr](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/af867915-534c-4e4a-bcb7-651dcbcfa438)


In the modern chip design industry many are going towards 5nm as the size of the chip will be reduced and also when the size decrease the operations will get conduted fastly. So the distribution of nm tech can be seen in the below photo![dis](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/51a5c50e-57de-411f-b9f6-f5c6ee030b20)


Since we are dealing with the 130nm lets get to know the fast of 130nm tech with some examples
(1)Intel:P4EE is a chip developed by Intel using 130nm which runs at 3.46 GHz
(2)Single cycle RISC-V 32i used by the OSU team has reported that it runs at a speed of 327MHz and with pipeline it will cross 1GHz.
#### Simplified RTL2GDS flow
The flow of the RTL to GDSII undergoes the following steps:
![flow](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/509da15c-f883-466c-a8c2-46702e56b5b3)

* Synthesis: Here the RTL code will get converted into the specified gate level logic/ netlist with the help of the SCL(Standard Cell Layout).The SCL will have the logic gates and upon the basis of RTL Code connections are done.Standarad cells have its own layout or model depending upon the EDA tool from which they are built.![syn](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/515bf006-94fa-48a1-8424-3f8241a55f5a)

* Floor / Power Planning:The main goal of the Floor Planning is to paln the silicon area effeciently and to efectively distribute the power in the circuit.
  * Chip floor planning:This type of floor planning refers to the partition of the die between different system building blocks and to assign the place to the I/O ports.
  * Macro Planning: Macro planning refers to defining the dimensions, pin locations and also the row definatons.
  * Power Planning: Power networks are constructed by connecting the vvd and gnd to all the components of the circuit with the help of veertical and horizontal metal rods.![ff](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e222dce3-114b-4fac-ae83-3feef20071b7)
 
* Placement: Placing the gate level netlist in the rows.Here the conical shapes should be placed close to each other to reduce interconnection delay.There are two types of Placement
  * Global Placement: This optimize the area and overlapping of the blocks will occur
  * Detailed Placement:In this the blocks are placed effectivily without overlapping
![palcement](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d7e7be8f-beaa-4727-9a55-1e54caafe173)

* Clock Tree Synthesis: Provides the clock to all the neccessary circuit components. The networ of the clock circuit looks like a tree. The circuit aims to have minimum skew rate.

* Route: Here we implement the interconncet using the available metal layers.Routing uses the inputs from the PDK file and uses the Lambda based rules for the conncetion and interconncetion of metals and others.SKYWATER130 has 6 layers of routing in which the last layer is called the local interconnect layer made by titanium nitrate layer, where the other 5 layers are made up of aluminium layer.There are 2 types of routing option available:
  * Global routing: Generates routing guides.
  * Detailed routing: Uses the routing guides and does the actual wiring.
![routing](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/65ddf1f8-b493-48e5-980d-2b02e4ae31a9)

* Signoff: This part deals with the verification and testing of the model.Testing such as DRC(Design Rule Checking), LVS (Layout vs Schematic), Timing verification, STA(Static Timing Analysis) etc are done.

#### Introduction to OpenLANE and Strive chipsets
OpenLANE: It is a open source model for RTL to GDSII flow and it comes with the APACHE version 2.0.So it is a free open source media where we can use it in the way we want.It started as an Open source flow for a Tape-out experiment. The main goal of OpenLANE is to produce a clean GDSII with no human interaction.It comes frome the striVE family which has Open PAKS, Open EDA, Open RTL in it.The family of the striVE can be understood in the below figure
![gen](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4e75f2ab-e391-451f-bf56-62b5e421a52d)
It supports SkyWare130nm and also XFAB180 and GF130G.It is used to generate Macros and Chips.The two modes of operations are Automous and Interactive.It comes with large variety of designs. At present 43 designs with their best configuration is available.

#### Introduction to OpenLANE detailed ASIC design flow
OpenLANE is based on many other open source projects such as OpenROAD, Magic VLSI, KLayout,Fault,Yosys,QFlow,ABC.The detailed flow of the ASIC can be seen as
![flo](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f86b043e-276f-4529-a9fc-eb6e77494b3b)
* RTL synthesis: This program is carried out by Yosys and ABC, where ABC will be having abc.scripts as synthesis stratergies to create the netlist with the help of SCL
* Synthesis Exploration: It gives the report on how the area and the delay are affected with accordance with the synthesis stratergies.
* Design Exploration: It gives the design configuaration and generates report which includes over 35 differnet design matrix.![design exp](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/105485af-921b-48c3-903a-b4b48324910c)

* Regression Testing: Here we can run over 70 different best design snaf compre reults to get the best known ones.
* DFT(Design for Testing): It is a optional setup and it uses Fault App  where it does scan insertion,automatic test pattern generation,test patterns compaction,fault coverage, fault simulation.![dft](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/bc4e6f4b-49b6-4c93-8d60-599aaf073fd7)

* Physical Implementation: It is also called Place andd Route.It uses OpenROAD.It includes Floor/Power planning,end decoupling capacitors and tap cells insertion.It includes the steps such as placement,post placement optimization,clock tree synthesis,routing.
* LEC(Logical Equivalence Checking):It checks the proper working of the logic every time the netlist gets modified.
* Dealing with Antenna Rules Violation:When the metal connection is too long,the metal rod works as a antenna and attracts the ions towards itself which will leads to the damage of transistor.So in order to overcome this we use two methods:
  * Bridging:High level Intermediators are attached.
  * Add Antenna diode: Add false diode to the circuit.While testing in Magic if it gets detected then replace the fake one with the original.![ant](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/cea723ae-af9b-455c-af7c-f24b083fe90b)

* Static Timing Analysis: Gives the timinig report which includes timing violation etc.
* Physical verification includes the DRC which is arried out by Magic , Layout is done through Spice simuklator and LVS is tested using Magic and netgen.

### Get familiar to open-source EDA tools
#### OpenLANE Directory structure in details
Some of the basic commands and some abbrivations which we see in Linux:
cd = change directry
ls = list
ls -ltr = list in chronological order
ls --help = list of all the command statements
clear = clears the window
../ = back to previous directory
skywater130_fd_sc_hd , here skywater130 refers to the tech and fd refers to the foundry ,sc refers to the standard cell,hd refers to the varient of this model

Now let us see the options and other things present inside the pdks
below photo shows the path for pdks ![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/344c0699-79f2-4aa6-8e30-17f5c6e46c1d)
 
Use of help command can be seen in this photo![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/02640820-880c-4bab-9284-b33587c1b12e)

Inside the pdks we see the skywater130a and its technical and reference libraries![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e6bec37a-5edb-46be-a0ad-ea9ce048e851)

The below photo refers to the reference of libraries and how the timing details are shown in lib![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0d7ca15e-8e20-4977-900a-5290e6f04440)

#### Design Preparation Step

Here we are going to open the openlane and to get the neccessary packages for that we use the commands as shown in the below picture![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/6016f8ad-dcff-46b6-bcd8-f6cd0b54a67d)

After this we can see check the number of designs in the openlane like this![ubu1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c3f60e42-f1d6-49d4-bcf2-310fb9ca5517)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/acd42938-81d9-467c-82c1-2d61578a567a)

In the design we are choosing the picorva32 core which will be having all the instructions set commands in the src![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1cf0f052-8956-4a27-9af0-537c2ef24cce)

The below image shows the config.tcl which will be having the information about the clock speed etc![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7113dc5d-fbcd-4877-a7ce-35076c1f1580)

Once the preparation is over we can see a new file in this picorv32 as runs and due to prepare all the lefs will get merged into one![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/da3eeef1-b0a9-4ade-bb79-d210753e4aa2)


#### Review files after design prep and run synthesis
After the preparation the "runs" folder will be having the below documents in it
![ubu5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f3f2ae88-a9e5-4dfd-8a78-6e4b9b305449)
In order to access the run use the date of the creation of the folder.In that we can see "tmp" and "results"  where we can see all the physical implimentation reports.Before synthesis all will be empty.
The "merged lef" in the "tmp" will give us a report like this![ubu4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3f202fa1-cfde-4ae5-8c04-ef5e5778c9d2)

For the synthesis to take place give "run_synthesis".The result can be seen like this
![ss](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a9dac2bf-961e-4601-86b5-3d3510a59427)


#### OpenLANE Projectr Git Link Description

#### Steps to characterize synthesis results
