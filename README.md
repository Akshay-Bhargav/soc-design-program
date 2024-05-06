![WhatsApp Image 2024-05-07 at 1a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3ed7f894-9f47-4b18-8e78-1392a353e846)# SoC-Design-Program
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

Assignment to calculate the flip flop ratio

Flip flop ratio = total number of DFF divided by total number of cells
![ass](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/00aa1f46-9435-49d3-b1a8-f25c51b944d6)

FF ratio = 1613/14876
FF ratio = 0.108429.

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


In the configuaration the floorplanning.tcl and readme files looks like this ![ff tcl in config](https://github.com/Akshay-Bhargav/soc-design-program/assets/168160665/044a3584-77ae-4671-a9f3-11aa06cf50e1)
![readme file](https://github.com/Akshay-Bhargav/soc-design-program/assets/168160665/00adf7ae-66bd-4f78-9927-71ddd523d89d)

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
* V to fit the selected layout to fit into centre
* Tap cells are used control the latch up condition.Here the N-Well to the Vdd and substrate to the Gnd.

The Layout can be seen like this in the Magic![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/94e0de46-1e5c-42f7-a513-7de39c90072a)

In order to select the pin just palce the cursor and press S.
The Pin layers and the dimensions along with the co-ordinates are seen like this![pin layer](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/5ea7a94f-082a-4918-a4bd-dd2b7bebc817)

The below picture shows the pin saperation.
![metal seperation](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c284d6a1-012f-4371-a993-5a995fb57d25)

### Library Binding and Placement
#### Netlist binding and initial place design
Now we have to provide a proper shape and size for the gates.It is done with the help of Libraries.
The Cell libraries look like this![cell](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/56232254-7de0-41db-b857-e81dd6d09892)

Libraries will have the inforamtion about the shapes and size,timings,delay information of a cell and contains many more cells in it.

The below picture of the cell, ciruit and the power planned core
![placement](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e16cf06a-1866-4778-9e34-f2d3e648f208)

Now we have to forward with the placement of the cell in the core.
The placing  ciruital components![placement](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/66a493a5-1b5e-4d40-8eed-5a76f5a73602)

#### Optimize placement usning estimated wire-length and capacitance\
Repeaters are the buffers which helps in signal integraty and helps to communicate with the long dstance components to communicate.
Based on the wire length and capacitence value we insert the buffers.Slew depends on the value of the capacitor.
The optimization done to the ciruit can be seen in the below figure
The 1st part of the ciruit doesn't need any optimizaton since the length is sorter   ![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/015b4334-6853-4dcb-804f-c31324066ff2)

For the 2nd part of the ciruit the optimization in placement looks likek this
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9060f922-666a-4df5-9c14-0e64f3465450)

#### Final placement optimization
The 3rd part and 4th part of the circuit can ba optimzed as shown in the below figure:![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/310ef008-33ee-413c-82bf-0530ec4d9ade)
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d7e247db-44f0-48a4-b432-2618bf26a861)


#### Need for libraries and characterization

The steps we follow while desiging the chip is like this![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/6325aa1f-1da3-460d-91c3-a5a40fdc8b64)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e8ad4a22-a561-4f36-b246-8db6682c7b75)

Libraries will be having the gates and logical circuits in them in a format which can be understood by thte EDA tools.

#### Congestion aware placement using RePLAce
run_placemect = to run the placement 
Output shown after the placement
![placement done](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a44d9006-d2f8-49ee-bcfa-f34e5a9fc376)

Path to check the placement in layout:
![check placement](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/186127e8-d1ae-4577-9147-710200570829)

Layout in MAgic and the Standard cells in the layout are shown in the below figure![magic layout](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c9ae0b56-f42a-4077-a365-6323e2c88eda)

![sc](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/65435615-9664-443d-8d72-110f372b4586)

### Cell Design and characterization flows
#### Inputs for cell design flow

Each standard cells such as AND GATE, OR GATE, INV have their own cell design flow.
The cell design flow consists of 3 parts namely 
* Inputs
* Design Steps
* Outputs.
Inputs includes
  - DRC and LVS rules
  - PDKS
  - SPICE models
  - Library and user defined specs.
DRC and LVS rules are
![drc](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3d73574c-3835-44d4-9231-13483c4956fc)

SPICE models and parameters are
![spice](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9ec96ec9-1ca6-48e3-aa39-621495fe30c4)

#### Circuits design step
Library and user defined specs defines:
* The cell height:The height of the cells is defined by the powelines and one has to design the cell with required drive strength with that defined height.
* Supply voltage: The top level design will mention the voltage level for the ciruit and the library developer has to develop the cell working for the specific voltage with considerations of the noise margin.
* Metal layer:There are specific rules while placing the different metal and other layers over each other.
* Pin locations: Library designer should be sure about the pin locations and the rules for presenting the pins.

The Design setps include 3 parts:
   - Ciruit design
   - Layout design
   - Charcterization

Ciruit design should follow  the combination of PMOS and NMOS to get the logic and their width ratio.Output of the ciruit design is CDL(Ciruit descriptive language).
![schem](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/502110a2-1a92-4506-ab2f-a1476a256a1e)

#### Layout design steps
It should follow  the circuit diagram, the graph of NMOS and PMOS Euler's path,stick diagram
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/079b793e-05ff-44f6-b1d1-09ffd6831bd1)

The output of the layout design will be GDSII,LEF,extracted SPICE models which contains the parasitic cap and resistance in the layout
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/510f15d6-9f7e-41fd-b59d-27a81b4a80ca)

#### Typical characterization flow

Consider the example of  buffer layout.
![11](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/226fc5c5-f8d8-4619-bd47-8be7cfe14d97)

SPICE netist consist of the resistance and capacitance of the layers and also the sub ciruit of the main circuit.ALso we will get the NMOS and PMOS sPICE models.
Chracterization flow consists:
  - Readin the Modelfile
  - Readin the extracted SPICE netlist.
  - Behaviour of the buffer
  - Read the sub circuit of inverter
  - Attach the power source
  - Apply the Simulus
  - Output Capacitance
  - Necessary simulation command

![22](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/956d7788-9db8-49eb-b3ea-4a5b17400d59)
![23](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e8ecb476-f7f5-4511-a1fa-3d0f3cec7cd8)

Now feed all these into GUNA a characterization software and the software carry outs the timing,noise and power function.

### General timing characterization parameters
#### Timing threshold definations
* slew_low_rise_thr
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/5d3dd4b2-8453-462f-b152-1f90172b6e96)

* slew_high_rise_thr
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/44c5ef80-feb6-456d-9edb-24ec11be8e41)

* slew_low_fall_thr![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/295f8ed2-9214-4143-94f4-1e6df6c20921)


* slew_high_fall_thr
  ![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1c2d828c-5b3b-49aa-8e47-b9bf4801dacf)

* in_rise_thr
  ![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/117aba48-5e2b-4cb1-8834-192bea64e7a4)

* in_fall_thr
  ![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4816b7ee-6b68-4a19-b2d2-3981dfbb7757)

* out_rise_thr
  ![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ef20181d-b3a4-49df-9bad-725d5b494b72)

* out_fall_thr
  ![8](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/21fc568c-ed26-448f-a2f7-d4b4154b04bd)

#### Propogation delay and transition time

delay = out(any thresholds) - in(corresponding threshold)
To margins at which we need to take the threshold values
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d3dd17a6-fe24-4d2b-bd4c-f87f41b9d2f9)

A delay can be visualised as shown in the below figure
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/22d01309-3b8d-4a70-b573-d65e1d7e28e7)

## Day 3 - Design library cell using Magic Layout and ngspice characterization
### Labs for CMOS inverter ngspice simulations
#### IO placer revision
This has 3 modes 
* 0 = unequidistant ports
* 1 = equidistant ports
* 2 = compressed ports
To set this mode give command as shown in the below figure

![VirtualBox_VDSWORKSHOP_05_05_2024_00_48_28](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/bfed14d7-0043-4c4a-b52f-6acbcd5e7915)

The output of the mode 2 looks like this
![com](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a60a766d-f791-4a76-99de-1036571d526b)

#### SPICE deck creation for CMOS inverter
It has connectivity information, inputs, tap points information
Consider the ciruit and the component value as shown in the figure
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f4524f26-82c3-4387-83aa-a0d5f2853d22)

Then later Identify the Nodes and name them
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/096d4eeb-ece2-4965-8e58-2e248b3f40f5)

* In SPICE * = comments 
* The netlist description of the circuit can be given as shown in the figure
* Here the syntax is M1,drain,gate,substrate,source,type of transistor,width,length
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c11bffaf-057d-4cf3-a8bf-61fc8728076c)

#### SPICE simulation lab for CMOS inverter

* Syntax for connecting the other components = starting node,ending node,value
* Simulation commands includes the interval from where to where the voltages are given and the step size og voltage.
* Next step is to include the model file which contains the description of the transistors related to the specified technology.
* The description looks like this
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/23e1bd53-3d75-4fa4-a5a4-2aa8e65fcf56)

Conisder the below example of SPICE Simulation
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4ee258b4-ecf5-4546-a489-99f83031051e)

Steps in the simulator
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/623846a6-10a7-413b-ba17-e68c7a164f18)
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/625d58a7-4e1f-44a2-8954-46a1da20741c)
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f04bd210-f574-4fcd-9f2e-296727f8f21c)
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/b66f05e5-02e0-4dff-aa30-cb75a87d6548)
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7aa09cfd-e3ea-4e3f-920a-d370952001d8)
![8](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/363b40cd-90f4-4eb3-aec1-bd0f399f722d)

![9](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ba22f5ea-6760-42b7-879b-b25b8865d6c6)

The output looks like this:
![10](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/34a140e1-a221-4807-a606-294e1405f09e)

Consider another example
![11](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/41739d08-20dd-4290-9bcb-28f2d12781e9)
![12](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9f725edb-77a0-4da8-beea-56d20ebdb599)

Output will be like this
![13](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/66bf422f-94e7-4935-8999-b1395bbb8aeb)

#### Switching Threshold Vm
The above examples output looks likes this
![a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c7625f5a-c730-4bc9-93f8-f172347f5bc2)

The Switching threshold can be visualized like this
![b](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9982c253-c60d-41ea-a41e-3fbd207c1591)

Regions of operations of transistors
![ca](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/02a22dd7-ae05-40b8-9042-f542e7290656)

#### Static and dynamic simulation of CMOS inverter
Now let us calculate the rise and fall delay for the given specifications


![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1dacdba4-ce38-437d-8977-2162f0c8da14)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/feec18ee-5998-4ce7-aecf-8848dfe47a66)

The output waveform looks like this
![3a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/77eb1ca0-f627-42b6-95c9-21a8c3ddaca6)

The falling delay co-ordinates are
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/6b79bc2a-7167-43b2-9f6e-28a87e5228dc)

The rising delay co-ordinates are
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d612cc02-21bd-4e3e-9f63-5889d3046cbb)

The results look like this:
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/055e437a-38e3-4b73-b429-bbfcf7dc9658)

#### Lab steps tp Git Clone vsdstd cell design
Here we are going to clone the github to the Open lane 
![git path](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d6d1ef00-
04f2-40f0-9221-9a3a5770fcd8)

After this we will get acess to the github contents. In order to implement the inverter in the github we will add the tech file in the OpenLANE to the new window
![adding to tech](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/fe3f1aee-5dab-414e-bd57-3eee8b6fef7d)

The path to implement the inverter in the magic
![path](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/779df56c-5951-417d-9e92-0d42da8fda1d)

Layout of the inverter implemented in the Magic looks like this
![inv](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/78b8345e-9fc2-4f8c-9a16-dc227f5cb1c1)

### Inception of Layout CMOS fabrication
#### Create Active regions
16-mask CMOS process.This process several steps such as
* Selecting the substrate and the doping concentreation![1a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/498a8788-0bfd-4203-b87c-a068a83b62b1)

* Creating active region: which includes applying 3 layers over the substrate and conducting photolithography.For the first time we use the mask in this step.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/bb1db356-d264-4741-80b8-0dab864605ad)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/712dc32c-59f7-428a-bd68-4e8dd766935d)
 
After the exposure to the UV light we will etch out the masked region
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/32542f1d-6bb0-4f0f-bc86-b8297ad16a7c)

Photo reisit will be chemically removed followed by washing
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/fb0c3386-aa9d-433a-9495-df1003fc1e2c)

![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/be7901d0-3b42-4fb2-9a2d-f400518df0e5)

Field oxide is grown over again
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3e4016dc-c968-4d2a-9ae7-1cdbbf0c91b2)

Because of this Isolation nodes will get created which will separate the transistors
![8](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a4756eb4-3293-4a64-b62a-fc14aa80fac5)

Acid wash to remove the above layer
![9](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/887a25e3-3653-4bbb-9b13-6f179c1b50f1)

#### Formation of N-well and P-well
The 3rd steps is the N-WELL and P-WELL fabrication.It will be carried out as shown in the below photos.
* In the 1st step we do the second masking which allows us to create the P-Well as shown in the figure
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/81f2612d-46a2-40b4-a076-3ca8d5652125)

* Layout view of the mask![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/24a46664-156b-483a-9a72-b83483d9b4c7)

* Here Photolithography will be done.![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e8fc0587-d979-45de-b4d9-3e6c5288349b)

* The unmasked layer has been etched out![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/69de8bb7-427d-4726-b951-9e75f2bd4e7a)

* Boron has been ion implanted into the substrate![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/619200b7-da5f-4226-8451-6ed4c4b04a9e)

* Same procedure is carried out for the N-Well with mask 3,  where phosphorus will be ion implemented.
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/b98e73ac-e691-4828-9827-306c31cc442f)
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d953d86d-5e2d-4daf-be4e-1c89d00fe85e)

* In order to penetrate the N-well and P-well deep into the substrate, it will be kept in the high furnance at  a temparature of 1100 degrees.
![8](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/27fe8188-15b6-4bc1-8195-b5eff8ddabe9)
![9](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a68fb39f-9a12-4131-a86c-27331f8400f9)

#### Formation of gate terminal
The important SPICE parameters for the gate terminals:
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1d0707c9-13fb-473e-9859-f8eef208b10a)

Now increase the concentration at the top layer of p-well and n-well with the help of mask 4 and mask 5.
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/728859cd-d6d8-4e99-8796-4316db33b022)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/48e4452d-76c7-4077-bdd8-b4784d96a0b0)
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/27c27189-48a1-490f-aaa9-112de37a42a8)
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/3f42c29f-f0ad-4fc2-91e9-06f64becc3b2)

Remove the oxide layer and place a new oxide layer of same thickness
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/08906f18-7b60-4469-81eb-5e84d3447d75)

Place polysilicon layer over the oxide layer
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/6aada5c6-8c33-4095-9dce-a4322f5623c3)

Create gate terminal using mask 6
![9](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/26435f09-7a6f-4e63-bdbf-81cf8503d4ba)
![10](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/dd1f5863-8aeb-450d-90c1-fab808defb11)

#### Lightly doped drain formation
Plasma anisotropic etching id the process where except the content in the side wall all other porstions will get etched out.

In order to create the LDD we implant n type and p type materials into the respective wells with the help of mask 7 and mask 8
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/609d344d-1553-4804-9399-fcd15b8a51f6)
![2a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/55b71d7a-1340-4be4-8a32-8aeded6927d4)

![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ee52d7bb-ccfb-43f9-89fa-db98f2d038a8)

![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/38e945af-44fd-458c-bd01-e53a9e46116d)

Now we do the Plasma Anisotropic Etching
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/dbb922e9-9e04-4e64-a30a-b86663728a6f)
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/fa0fb824-2d94-4985-8676-e2a24af43176)

#### Source and Drain Formation
Here we create the source and  drain terminal using 2 more mask and at last we will do high temperature annealing.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e641e8a6-f57e-4ac7-bbe3-9492b14b7719)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/124fb35a-2fea-4eab-8fcf-b8df900edf4d)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4a35c4d3-ff9b-4150-b33d-669340cf9319)
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/373e57b0-561c-472d-8a1a-d7a1d30541e0)
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/02a034f9-3289-43ad-aa12-47ea315c3f32)

#### Local interconnect formation
In this we create the metal for the connects.We use a layer of Titanium followed by heating in the presence of Nitrogen which results in another layer.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f99ee2e1-d6cd-4ebd-a0c3-379e4f4630f6)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/9dc59877-82fa-4516-93fb-47a4e8b878d6)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/680aeee0-6686-4aa8-8b63-f8ed0764dc3d)

After this we etch out the unnecessory portion with the help of mask 11.TiN is etched using RCA cleaning![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/02079164-f2a8-4809-a2c0-9d0dfa848c3d)
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/fc9ad821-d479-4123-8c24-206d0998018f)
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7768991e-d229-4e5d-a405-989fb0307832)

#### Higher level metal formation
Place a layer of silicon dioxide with Phosphorous and Boron which is called as Phosphosiicate glass.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/dcb6812d-c998-459d-a8b8-f5d5a64b674d)

After this undertake the Chemical Mechanical Polishing
![2a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7dc6dbdd-bd18-4ae2-88f0-1971235b6d86)

Create the contact holes with the help of mask 12
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/624e90e1-6402-4f61-9461-9b0dcfddae4c)

Place a Titanium Nitrate which works as a barrier followed by Blanket tungsten layer and again do the CMP.![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/82ff2e54-3807-4a34-a6c9-3638f49fe46f)


Place Aluminium layer and conduct the masking to get a Aluminium layer at particular part
![4](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2f3eca24-24e9-434c-b026-27979690b578)
![5](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a45de6e1-bc2d-4088-aaed-6875265f7814)

Later  place the oxide layer and create a hole in the region of Aluminium with the help of mask 14.Place the titanium and tugstan layer and palce the aluminum layer with more width. Use mask 15 to define the area of Aluminium.
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/82234e06-e827-44b1-8c9e-0425c4ce3cf9)

Last layer is of dielectric and using mask 16 for the contact of aluminium
![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/364f6e25-5eb3-4afd-8381-fc62e62da7b8)
![8](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/21faea1b-c0bb-4c1e-8461-69a798c53393)

#### Lab introduction to SKY1130 basiclayers layout and LEF using inverter
In this section we are going to look into the options in the Magic
* Finding the layer name and the connection link
![nmos](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/efddc29d-ef29-4a14-b5d8-ba91cbed2775)
![pmos region](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/5b900749-9cff-433a-96e3-79022c981cbe)
![connection shown](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e5d4ab16-d524-4ed7-ac8d-fa1e78cc858f)

#### Lab steps to create std cell layout and extract spice netlist
Layers in the layout are
* Locali,N-well,nsubstrate
* A connectivity has to be dine between locali and N-well, locali and N-substrate and with metal(licon)
* DRC error
  ![error](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d978b46b-cd08-4ca8-9b07-f17df9c68a19)
![ticon](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/966dca01-c03a-4ea3-ab4e-2bffe4b71871)

* The important commands in ticon winodw are
 - extract all(extracts the layout data)
 - ext2spice cthresh 0 rthresh 0(extracts the parasitic capacitence)
 - ext2spice(conversion  of format)

* After this the Magic file will get extracted to the Spice format and we can see the new folder   
![done](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/12896cae-9fde-4a62-abb5-aeaf10ea32f9)

In order to open the extracted file "vim (extracted file name)"
Spice documnet looks like this:
![spice window](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/dbab86ca-f3f9-43f4-808c-c1cd2ba41d73)


### SKY130 Tech File Labs
#### LAb steps to create final SPICE deck uding Sky130 tech
* Define all the necessary components in the script.
* Add pmos and nmos library.
* Pulse syntax = Variable_name a b PULSE(start_voltage end_voltage starting_point rising_delay fall_time pulse_width time_period)
* This is the path for the pmos and nmos libraies
 ![nmos lib](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f4b5afc7-c2f5-471d-8e07-745c2153e27b)
* Inside the pmos library![inside pmoslib](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7623d79e-9a52-4ae1-819b-693cd4f2b647)
* Spice code![code](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c98a0bd5-25d7-44cf-8831-1758acae3c37)
* Simulation path of spice![simulation of spice](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4695efe7-bd08-419a-9107-b63fd85d4494)
* Spice output
![spice output](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f151e53e-e89d-4dfd-bb82-1bb73e3f5f03)

#### Lab steps to characterize inverter using sky130 model files
GRAPH CODE = plot y vs time a
* Output graph![output](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/49ff4a21-cd0f-4e1f-a2a6-0f08699d4b44)

* rise dealy =0.0363![rise transition](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/89a8ea60-59b5-4634-a5f2-8ec49fb46911)

* propogation delay =0.0368![propogation delay](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/667a5cf6-d1f1-4b72-a8a6-6fb9905bf4de)

* fall delay =0.0274![fall delay](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c05c9150-f9cd-4731-82e6-51698cf793c8)

#### Lab introduction to Magic tool options and DRC rules
Link to open the Magic http://opencircuitdesign.com/magic/
The MAgic is an Open source tool whose menu and other contents are shown in the below photos
![Screenshot 2024-05-06 032424](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2505c46d-658d-4946-bab3-8070885f7c3e)

Menu of the Technical part:
![Screenshot 2024-05-06 033158](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/500ccd8c-c605-4009-b0f7-cd1eaaf58c79)

DRC menu:
![Screenshot 2024-05-06 033205](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7c9f9521-8dec-4ff8-87ff-b941584733c1)

Cifoutput section:
![Screenshot 2024-05-06 033355](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/cfe6f621-df76-4626-bbc4-ad2df46760b2)

#### Lab introduction to SKY130 padk's and steps to download labs
This section deals with the Sky130 manual ,rules of the Skywater etc.
Link to download from github wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tg

## DAY 4 - Pre-layout tin=mings analysis and importance of good clock tree
### Timing modelling using delay tables
####  Lab steps to convert grid info to track info
Track path and information inside the track
![track info](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/165caec2-83d7-4d37-b502-a976d128fae7)

![track data](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1f4c55c6-435d-42ea-8020-387d5c74fd3a)

Applying grid to the layout to show that the input and output pins are on the X an Y axis defined in the TRACK
![grid](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/67d0bd8f-10c1-489b-b131-ea5a4eb83384)
![output grid](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/66ba416b-ef3e-4231-8e38-e2d49a534b23)

#### Lab steps to convert magic layout to std cell LEF
The other condition is that the standard cell width and height should be the odd multiples of X-pitch![h and w](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/28298a11-50b8-4fe5-88c1-ed0cc36fc05e)

Creating the port using the variable![defining ports](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c2bb0477-6cc7-4d5b-9f09-bd85c87a7fa9)

Defining the ports![define port](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d6593d0a-6573-413b-8110-2b88f891eb0f)

Converting layout into lef file.
![creating lef file](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/18a10467-d5be-44a3-ac28-afd62d32ce28)
![lef file of the layout](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/606c8e29-00d2-404d-9158-fa18908dd271)

#### Introduction to timing libs and steps to include new cell in synthesis
Copying the created lef file in src to store it in the picorv32a
![copy lef to src](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/b80c52f6-d197-472f-a43c-02797aed2b3e)

Copy the cell information to the src![library](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/bb28eecb-5a2f-4027-974c-6d6d94fe904a)

Modify the config.tcl![modify](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4024d6aa-4227-4a01-8c8c-a92f3899ffe9)

Run the OpenLANE![to run the copied file](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4ac0bc7e-4a51-41bd-a0c2-543ebbf9a9b7)

Run the prepartion and Synthesis![synthesis](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/bcbf030e-7dd2-4d25-82af-fe99a5109247)


#### Introduction to delay tables
AND gate and OR gate are used in replacement to the inverter to reduce the repeatation of the clock.In the delay model all the sizes of the clock buffers at a level should be equal.We use delay table to each and every cell to build the dealy model of the circuit
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a92b93e3-b952-4300-94ae-14e961f5e6b2)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ca7419be-875a-48c3-b34f-423c6b424182)

#### Delay table usage Part 1 and Part 2 
In the Delay Table locate the point at which the input and output capacitance will meet , the value at that point describes the dealy of that gate for the given capacitance.Every gate has its own delay table.When the capacitance value is between some values in the table we form a equation and get the value for that value
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f8354a24-e563-4b39-9f26-232a3a4c3e30)
![6](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e46ff535-580c-4611-87df-26bf8646fef8)

![7](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d1f943ae-9646-4dd5-bec7-d012a655bb33)

#### Lab steps to configure synthesis settings to fix slack and include vsdinv

Modify the README.md file as per the need so that we can reduce the slack
![modifying the parameters](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7d4a10c8-63e5-4ab4-8ada-0fe1189a66b7)

Synthesis and run floorplan
![synthesis](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/77880e9b-0ba1-4856-8e08-982b580a8700)

Placement
![place](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4d299378-f618-4796-8e19-f29375646aad)

Layout

![layout path](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/c05ae01b-0432-4a6d-a5e6-e675172dbbba)

![layout1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/f472f72a-b567-4a0a-bffe-cd41c62fa0b0)

![layout2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/90dd29aa-5b30-4ebe-b244-d1c7375dfb18)

![layout3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/947fa73b-3ff6-477b-8d01-6b394adb5f3e)

### Timing analysis with ideal clocks using openSTA
#### Setup timing analysis and introduction to flipflop setup time

A combinational ciruit will be having 2 flip flops namely latch and capture flip-flop as shown in the figure![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a127bacd-e2d9-4218-812c-5c4061fc63d7)

The clock period is T to get the output at the capture latch.Therefore the delay at the combinationa ciruits must be less than clock period.But each flip-flop will contain 2 MUx which will be havin there own delay. So the capture latch requires some time to pass the value to the 2nd mux. So in total let us consider the delay generated due to the 1st mux will be "S" and when the clock period reaches T the 2nd mux will give the output. So the delay of the combinational circuit must be less than T-S.
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/63443db1-4723-422b-b75b-19a6435d98e5)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/7265f217-3efc-4617-a7ca-43c6398d3723)

#### Introduction to clock jitter and uncertainty
Jitter - It is the temparory variation in clock signal generated due to the clock ciruit.So in this case the clock may arrive fastly or may face the delay.So the total tim period will decrease.So for the clock period now we have to take into caniserations of the delay by the mux and also we need to consider the jitter.
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/ff39a919-b115-466b-a8b3-0c11ca7b5886)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/20b34364-e729-412f-a549-6bce18d136b6)

#### Lab steps to configure OpenSTA for pst-synth timing analysis
Create new file pre_sta.conf
![pre_sta conf](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2f00c357-3538-4cf2-984d-3c12627b93ef)

![prepath](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/aeea400f-a8cf-46f2-94fb-7e53d0175a65)

Create one more file called my_base.sdc
![mybase1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/87e912d1-138e-4c8e-ba79-ded42baec779)

Typical.tcl script
![typical 1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d0fe9c1a-9d7c-4b97-a503-f95dcbd9a2cc)
![path fo rtypical](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/04b82efa-b080-4205-b283-4d2bfaee6646)

#### Lab steps to optimize synthesis to reduce setuo violations
Here we reduce the delay of the nets with the higher delays
![synthesis](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/e12f7cbf-5973-45ce-a440-48012b235325)

![floorplan](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/4f85f5cb-d760-4aab-bfc7-1e1d0b962581)

### Clock tree synthesis TritonCTS and signal integrity
#### Clock tree routing and buffer using H-tree algorithm
Here we are going to implement the clock tree.When we directly connect the clock to the flip-flops it creats the skew so we follow H-Tree method to implement the clock
![WhatsApp Image 2024-05-07 at 1a](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/a228eae9-9ab8-424a-a565-220b94db902a)
![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/5aabb054-8bda-4e5c-99e8-da2695d6c7a2)

Even when we implement the clock in this format due to the length of the wire we may not get the required value or it may lead to the delay . so we use buffers to regulate all this.![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/1080834a-43c0-4223-9e4f-081680bc07b0)

#### Cross talk and clock net
Encapsulate the clock wires.When the clock wires pass through the other wires cross talk may happen which results in the delay of the signal.Shielding may result in glitch and delta delay. 
![1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d6603bf8-bbea-49bb-bd2b-afbb15532674)

![2](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/da74b1b9-6b9b-4565-b6f9-9505bd88e6d4)
![3](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/2019453f-6ced-4ff5-9c8c-548ea75f2bb1)

#### Lab steps to run CTS using TritonCTS
#### Lab steps to verify CTS runs
### Timing analysis with real clocks using openSTA
#### Setup timing analysis using real clocks 
#### Hold timing analysis using real clocks
#### Lab steps to analyze timing with real clocks using OpenSTA
#### Lab steps to executr OpenSTA with right timing libraries and CTS assignment
#### Lab steps to observe impact of bigger CTS buffers on setup and hold timing
