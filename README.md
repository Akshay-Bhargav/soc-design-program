# soc-design-program
## DAY 1 
### How to talk to computers
#### Introduction to QFN-48 PAckage,Chip,Pads,core,die and IPs
* Arduino Leonardo:
  Basically Ardunio Boards are the microcontroller platform which gives easy of communication between the hardware and the softwre. We can easily do the hardware comnections and can easily code the necessary code for the projects. Arduino Leonardo is one of the type of hardware-software platform which is based in on the ATmega32u4. This board inculdes 20 digital I/O pins and a crystall oscillator of 16MHz frequency. In the 20 I/O ports 12 pins work as analog inputs and 7 pins are Pulse width modulation outputs.It also includes a USB connection, a power jack, reset pin and the ICSP header.It can be switch on with the help of the adaptor and also by connceting it to the computer through USB cable. ![arduino-leonardo-board1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/14ffae04-199f-42d1-9a83-454208820a4a)

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
*  Pads : Pads are the medium through wich the input and output signals has to pass.
*  Die : Small block of semiconducting materials on which the Pads has been built and mainly refers to the cornors of Square patch.
*   Foundry IP's : Foundry will helps in providing the essential building block for the chip design,allowing the designer to leverage pre-designed components optimized for specific purpose technologies.
  
#### Intro to RISC-V
RISC refers to the Reduced Instruction Set Computer where V stands for the fifth generation of the architecture.The instructions given will be less and the instuctions will be simple.It consists of more number of general purpose registers. The RISC-V architecture provides the benifit of pipelining.The addressing modes are simple. RISC-V is a open source insturction set architeture which allows the user to customize .It takes single clock cycle for the execution of the instruction.The base instruction set has a fixwd length of 32-bits and the ISA supports variable length extensions where each instruction can be any number of 16 bit parcels in length.The memory usuage of the RISC will be high and also the price of the chip will be costlier than the CISC.

####  From Software Applications to Hardware
This section deal with how the signals are read by the RISC-V

When we run the application the commands  will get read through the System Software and then it will get passed through the Hardware.
![l1](https://github.com/Akshay-Bhargav/soc-design-program/assets/168112516/d702a8c2-661a-4867-9c61-85edb369d6ed)

*System Software:
 The flow of the insturction in the System Software can be divided into 3 parts such as:
  * Operating system:
    OS handles the I/O operations and place a crucial role in allotment of memory.It will be having all the details regarding the I/O pins configurations,buses,Interrupts etc. It will conduct low level system functions
  
  * Compiler :
   The inputs will be in a standard form and the user will do the necessary code or build the inputs in the high level language such as C,C++,Java,Python,HTML.When these inputs comes to the compiler it will convert the high level language into assembly level language.This output from the compiler is termed as the Instuction sets which will be in the .*exe file format and will be in hexa-decimal for RISC-V.The compiler will convert the inputs into the instruction set based on the respective forms of hardware.Instruction sets will act like a interface or bridge between the code and the hardware and thus it is called as Abstruct Interface.The hardware is dependent on these instruction sets so it is called as the architecture of the computer
  
  * Assembler :
   Assembler takes the instruction set which will be there in the assembly level language and converts it into the binary format or the machine level language which can be understood by the hardware. As per the output of the assembler the harware will generate the chip layout. The output of the assembler will be in binary form.

