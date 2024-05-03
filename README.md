# soc-design-program
## DAY 1 - Inception of open-source EDA,OpenLANE and Sky139PDK
### How to talk to computers
#### Introduction to QFN-48 PAckage,Chip,Pads,core,die and IPs
* Arduino Leonardo:
  Basically Ardunio Boards are the microcontroller platform which gives easy of communication between the hardware and the softwre. We can easily do the hardware comnections and can easily code the necessary code for the projects. Arduino Leonardo is one of the type of hardware-software platform which is based in on the ATmega32u4. This board inculdes 20 digital I/O pins and a crystall oscillator of 16MHz frequency. In the 20 I/O ports 12 pins work as analog inputs and 7 pins are Pulse width modulation outputs.It also includes a USB connection, a power jack, reset pin and the ICSP header.It can be switch on with the help of the adaptor and also by connceting it to the computer through USB cable.

 ![arduino-leonardo-board1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/14ffae04-199f-42d1-9a83-454208820a4a)

  Our objective of this course mainly deals with the chips or the processor as mentioned with the square box in the above picture.
Processors are the brain of the system which carry outs the programs,computes data, and coordinates the activity of other system components.It cannot work alone so it will be integrated with many more devices.

* Peripherals of the chip/processor :
  Across the chip/processor we will be able to see many more interface conncetion across the board as show in the below picture![processor](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/80568241-de26-4f3e-b6de-22bfa06ff785)

  Processor has been connected to many more interfaces such as to the JTAG UART which helps in the communication between the external devices without the mediating devices such as RS-232.Also it will be connceted to the SDRAM for the Memory,Flash,Voltage connection,Ground,ADC etc.

* Packages : IC Packages protect the semiconductor devices and components and helps in the integration of the IC with the electronic devices. There are different types of packages such as:
  * Through hole Packages: It is the type of package where 1 or more leads go through holes of PCB and gets connected using the solder.The other types in this are
    - SIP(Single In Line Package)
    - DIP(Double In Line Package)
    - PGA(Pin Grid Array)
      
  * Surface Mount Packages: This is the Package where the external devices are mounted on the PCB board.The most common technique used in this type are
     - QFN(Quad Flat No-Lead):These are compact sized,the model QFN-48 has 48 pins in it where the chip will be having pins in all the 4 sides.In the below figure we can see the QFN-48 packaged chip![pp](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ff015b50-e362-46cd-832e-5575ae7b8cab)
     - Ball Grid Array : Instead of leads in this we use metall balls to create the respective connection
       
  * Contact Less Packages: In this type there will be no physical connection between the PCM.

Inside the chip there is a Square Patch which has been divided into many regions as shown in the figure![fo](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0a1e9cc7-07c5-4c7d-93ad-daba667dd01f)

* Core : Area inside the chip where all the digital logic takes places with the help of the digital ciruits with in it.
* Pads : Pads are the medium through wich the input and output signals has to pass.
*  Die : Small block of semiconducting materials on which the Pads has been built and mainly refers to the cornors of Square patch.
*   Foundry IP's : Foundry will helps in providing the essential building block for the chip design,allowing the designer to leverage pre-designed components optimized for specific purpose technologies.
  
#### Intro to RISC-V
RISC refers to the Reduced Instruction Set Computer where V stands for the fifth generation of the architecture.The instructions given will be less and the instuctions will be simple.It consists of more number of general purpose registers. The RISC-V architecture provides the benifit of pipelining.The addressing modes are simple. RISC-V is a open source insturction set architeture which allows the user to customize .It takes single clock cycle for the execution of the instruction.The base instruction set has a fixwd length of 32-bits and the ISA supports variable length extensions where each instruction can be any number of 16 bit parcels in length.The memory usuage of the RISC will be high and also the price of the chip will be costlier than the CISC.

####  From Software Applications to Hardware
This section deal with how the signals are read by the RISC-V

When we run the application the commands  will get read through the System Software and then it will get passed through the Hardware.
![l1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d702a8c2-661a-4867-9c61-85edb369d6ed)

* System Software:
 The flow of the insturction in the System Software can be divided into 3 parts such as:
  * Operating system:
    OS handles the I/O operations and place a crucial role in allotment of memory.It will be having all the details regarding the I/O pins configurations,buses,Interrupts etc. It will conduct low level system functions
  
  * Compiler :
   The inputs will be in a standard form and the user will do the necessary code or build the inputs in the high level language such as C,C++,Java,Python,HTML.When these inputs comes to the compiler it will convert the high level language into assembly level language.This output from the compiler is termed as the Instuction sets which will be in the .*exe file format and will be in hexa-decimal for RISC-V.The compiler will convert the inputs into the instruction set based on the respective forms of hardware.Instruction sets will act like a interface or bridge between the code and the hardware and thus it is called as Abstruct Interface.The hardware is dependent on these instruction sets so it is called as the architecture of the computer.
  ![abst](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2ef3e745-f669-49a8-b62a-12182ab13445)

  * Assembler :
   Assembler takes the instruction set which will be there in the assembly level language and converts it into the binary format or the machine level language which can be understood by the hardware. As per the output of the assembler the harware will generate the chip layout. The output of the assembler will be in binary form.

* Hardware:
   Hardware Description Language ensures the conversion of instuctions sets into the binary format or to RTL language. Then after the instuction getting into the RTL format it will generate a netlist which includes the connection of the logic gates. Basically netlist helps in the gate level description of the code. AS per the netlist design the physical design gets implemented or the layouts will be built inside the chip.
  
* Code flow can be divided into 3 parts:
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
* cd = change directry
* ls = list
* ls -ltr = list in chronological order
* ls --help = list of all the command statements
* clear = clears the window
* ../ = back to previous directory
* skywater130_fd_sc_hd , here skywater130 refers to the tech and fd refers to the foundry ,sc refers to the standard cell,hd refers to the varient of this model

To open the openLANE give the code as "docker ./flow.tcl -interactive"

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

give "pakage required openlane 0.9"
Once the pakage is over we can see a new file in this picorv32 as runs and due to prepare all the lefs will get merged into one![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/da3eeef1-b0a9-4ade-bb79-d210753e4aa2)


#### Review files after design prep and run synthesis
For the preparation give "prep -design picorv32a".
After the preparation the "runs" folder will be having the below documents in it
![ubu5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f3f2ae88-a9e5-4dfd-8a78-6e4b9b305449)

In order to access the run use the date of the creation of the folder.In that we can see "tmp" and "results"  where we can see all the physical implimentation reports.Before synthesis all will be empty.

The "merged lef" in the "tmp" will give us a report like this![ubu4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3f202fa1-cfde-4ae5-8c04-ef5e5778c9d2)

For the synthesis to take place give "run_synthesis".The result can be seen like this
![ss](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a9dac2bf-961e-4601-86b5-3d3510a59427)


#### OpenLANE Projectr Git Link Description

Here a Introdction was given about the Github. In order to understand the OpenLANE we can go through a Github repository called "efabless/OpenLANE" where we can see the deatiled description of the OpenLANE.The Github repo of the efabless where the important concepts of OpenLANE are showcased like this![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0831864c-cd54-48e8-9a9b-fe45d6d903ee)


![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7e2153b7-34d8-4249-a1df-dbf06fde4007)

![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/51519ccc-388d-4fb7-a470-18590980675c)

![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1f8253a9-ee95-4117-ac97-dd7424b8b25e)

#### Steps to characterize synthesis results
After synthesis now we are going to check the results and corresponding reports.The result of the synthesis is going to look like this 
This is the path for the result of synthesis![12](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/83188806-84d9-44a9-b6d7-f524c5e9355d)
 
Output in the synthesis window![10](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3626b40c-422a-41a4-afcb-92eece10199c)

The reports regarding the synthesis can be seen through this path
![13](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/8eed685c-c0dd-4f72-bee7-8fdd9758568f)

The different types of reports in the Synthesis are
![16](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3d761e53-7cbf-43fc-8854-02a8e5f287d6)

Synthesis stat report will be generated in this form
![14](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/b7aec4f5-7508-48a2-9561-4906a1a8a6e7)

Synthesis timing report will get generated like this
![timing dealy](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ad6fc67f-3d06-4449-8db9-469fd48d54e8)


## DAY 2 -  Good floorplan vs bad flooeplan and introduction to library cells
### Chip Floor planning considerations
#### Utilization factor and aspect ratio
* Netlist defines the connectiviy of an electronic design.
Netlist represents the gate and the connection between them.Consider a netlist as show in the figure
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e5f114cc-579b-4f53-877a-67f1a393961f)

In the chip on the silicon wafer we build the core inside the die as shown in the figure 
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/20b61182-09a2-48be-b353-f65aead4fe70)


Now consider all the standard cells have the same dimension and the minimum area taken by this netlist can be shown like this
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0e2c90ee-4c3a-4d73-8766-a62fa167201c)


Utilization factor is the ratio of the Area occupued by the netlist to the Area of the core.If the netlist occupies the hole area of the core then it is called as 100% utilizaton of the area and the utilization factor will be 1.In the practicle senerios  netlist uses only 60% or 70% of the area..When the utilization factor is not 1 it significe  the occupied area and we can use the remaining area or optimize the area as per our need. Aspect ratio is a another term which is the ratio of the height of the core to the length of the core.Whenever the aspect ratio is 1 till tells that the chip is of square shape.If the ratio is of some other number then it significe that the chip is of rectangular shape.

Below figure shows the Utilization ratio and the aspect ratio for a example:
![41](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9819b7a7-757e-4474-969d-960eca875e99)


#### Concept of Pre-placed cells

Pre Placed cells are the blocks which contains or defines a certain logic as shown in the example![1a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2b55dd48-3574-4a7f-9c49-dece56f77061)

Here each part of the ciruit it been divided into 2 parts and each circuit is declared as a block and it can be seen like this![1b](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/477d82c1-9cae-4625-b098-cd1e8fd92300)

![1c](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/0b0d1a25-308b-4aab-bfa7-f9dfc041d1ae)

Commomnly available IP's in the market are Memory,Clock-gating cell,Comparator,Mux.

#### De-coupling capacitors

When the ciruit elements needs some specified voltage to get activated but due to the complexity in the ciruit there might be a voltage loss .So in order to solve this we use the decoupling capacitor which will be placed alongside the ciruit with the same voltage as the source as show in the below photos.
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/85b9294e-9dd8-444f-9de1-fca86dbcff9a)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a0b33eb6-ff5f-4e15-a049-f8e045061ed6)

While placing the blocks segregate them in terms of input side and output side.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f497828a-7581-4ebc-b82e-23c737b8eb12)


#### Power planning

When many capacitors start to discharge to a common ground then the ground line many face "Ground Bounce".When many capacitors starts to charge at a same time the voltage line will face "Voltage Droop".This problem can be solved by having multiple ground and soucre terminal.So all the outputs will be connected to either vdd or gnd and instead of taking inputs from the other bloks output now the blocks will take the inputs from the vdd and gnd lines.Consider the following exapmle circuit we can optimize  it as shown in the below photos:
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/20dcd4cc-888a-4f58-95ef-2d3723888837)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/84038454-dc28-4363-abe0-17c2a3d01ee8)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/79d2b0d1-8906-4951-a35d-fa80c0c9a21c)

#### Pin placement and logical cell placement blockage
Clock port will be in bigger size than the pin ports in oreder to decrese the resistance.After the port installation block the contact between the ports.Now as a continuation of the previous power planning we take a exmple circute for the input and output considretaions as shoen in the figure:![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4373a11b-9dc3-4e53-a73c-267ff80f4778)

The Pin placement will look like this for the above circuit
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d6216315-f5b7-4c84-a31d-0139e235fa0d)

#### Steps to run floorplan using OpenLANE
* run_floorplan = floorplanning command.

For the floorplanning first let us see the configurations in the OpenLANE
![config](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/5a590592-1b0a-4135-9f69-676341a6c98d)


In the configuaration the floorplanning.tcl and readme files looks like this ![ff tcl in config](https://github.com/Akshay-Bhargav/soc-design-program/assets/168160665/044a3584
![readme file](https://github.com/Akshay-Bhargav/soc-design-program/assets/168160665/00adf7ae-66bd-4f78-9927-71ddd523d89d) -77ae-4671-a9f3-11aa06cf50e1)

#### Review floorplan files and steps to view floorplan
* def = design exchange format.
* 1 micron = 1000 database units as per our design.

Path to check the result core utilization in the floor plan and checking whether the core utilization followed the presedence.
![checkign2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ecd21beb-9559-4961-9d7d-e7fd16f9eac6)

The unit and coordinates and components will be seen in the resuls followed by floorplan then in the def file. The result can be seen like this
![units and coordinates o fthe die](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4378174a-6d2a-4c0d-a28d-360cab23d8f9)


Now we will see the layout of the specifications through the Magic. The Magic will be present in the skywater130A of PDKS. So take the route of magic and the path of the merged lef and also the result flooplan as shown in the figure:
![path for magic](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ce2e8fb2-cfdf-4c3a-9689-f47900fcf6de)

Magic tool will pop up like this

![magic](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a6bae0c5-c824-43b3-a533-12e8fbe821c2)


#### Review floorplan layout in Magic
* Q+S to select the layout
* V to fit the selected layout to the centre





