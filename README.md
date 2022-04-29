# RTL Design Using Verilog With SKY130 Technology
![1](https://user-images.githubusercontent.com/64180927/165375376-94d67619-5b34-45b4-8a59-cec5eb493610.png)
### This is a report that is submitted as an evaluation for the 5 day workshop 
## *Index* 

- [RTL Design Using Verilog With SKY130 Technology](#heading)
  * [About This Workshop ](#sub-heading) 
  
- [Day 1 : Introduction to Verilog RTL design and Synthesis ](#heading1)
  * [ Introduction to open-source simulator iverilog](#sub-heading1)
    + [Sub-Part 1 : Opening iverilog and visualising an example code using GVIM  ](#sub-sub-heading1)
    + [Sub-Part 2 : Running the multiplexer example  ](#sub-sub-heading1b)
  * [ Introduction to  Yosys and Logic synthesis](#sub-heading2)
    + [Sub-Part 1 : Giving input files to the yosys synthesis tool ](#sub-sub-heading2)
    + [Sub-Part 2 : Running Synthesis  ](#sub-sub-heading2a)
    + [Sub-Part 3 :  Visualising the generated  Netlist  ](#sub-sub-heading2b)
 - [Day 2 : Timing libs , hierarchical vs flat synthesis and efficient flop coding styles ](#heading2)
  * [ Introduction to dot Lib ](#sub-heading3)
    + [dot Lib Part 1 : ](#sub-sub-heading3)
    + [dot Lib Part - : ](#sub-sub-heading3a)
<a name="heading"/>

## RTL Design Using Verilog With SKY130 Technology 

<a name="sub-heading"/>

###  About This Workshop  
The main aim of this workshop is to have a good understanding of how RTL Design and Synthesis is done in Industry.Very good emphasis is given to practical learning. In this workshop very good coverage of practical open source tools like iverilog, GTK Wave , YOSYS synthesizer. This course is done on SKY130 technology. Very good resoruce for learning how synthesis is done practically. 

<a name="heading1"/>

## Day 1 : Introduction to Verilog RTL design and Synthesis 

<a name="sub-heading1"/>

### Introduction to open-source simulator iverilog
iverilog is an open-source EDA tool simulating the designs that we code using Verilog HDL language. The tool can be able to run the simulations and with the help of waveform visualizer like GTK wave we can determine if our design is working properly.The first part of the course starts with how to use this iverilog.The following figures describes what are the thing that are done during lab session.
<a name = "sub-sub-heading1"/>

####  Opening iverilog and visualising an example code using GVIM
As a first example we are simulating a simple multiplexer. The verilog code is present and using iverilog and GTK wave we simulate and observet the functionality of the multiplexer.

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165847175-73d3e6c1-a18a-44d2-b792-49e3415d60b2.png" width="500" />
  <img src="https://user-images.githubusercontent.com/64180927/165847057-63fd57ee-afb6-42f8-bb89-40ad8c684f9d.png" width="500" />
</p>

<a name = "sub-sub-heading1b"/>

#### Running the multiplexer example
Using gvim we can viualize are is present in the verilog files. As shown below the snapshots of both RTL Design of multiplexer and the testbench is shown.On the figure on Right side simulation results are visualised in GTK wave.

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165848008-fc95f6aa-9f0b-430e-bcd4-6f385f9e11ca.png" width="500" />
  <img src="https://user-images.githubusercontent.com/64180927/165847682-b0bc36dd-4e70-4948-bf2b-e73e7d9b2f6f.png" width="500" />
</p>

<a name = "sub-heading2"/>

### Introduction to  Yosys and Logic synthesis 

After simulation is done using the iverilog and ensuring that our design works properly , we need to generate a netlist. This done by mapping the components (various standard cells, pins, I/Os) which are given by the foundary are mapped based on our design. During this stage the yosys EDA tool optimizes the design.Various optimizations that are done are explained in this review later. So, the final output of the Yosys tool is the optimized netlist.To the Yosys tool we give two inputs , they are the our design which is in the form of .v code and a lib file (here from SKY130 technology) is given to the tool to generate the optimized net list. This whole process is shown below 

<a name = "sub-sub-heading2"/> 

####  Giving input files to the yosys synthesis tool 
<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165850815-ff5a59bb-b3ec-46c0-b9e5-b0e2fef161c5.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165852012-90dd2c22-66e0-4262-b7b4-fa4c1426a064.png" width="500"/>
</p>

<a name = "sub-sub-heading2a"/> 

####  Running Synthesis 
After giving the tool our designs and library we now use the synth command to synthazise the design. The tool then uses various algorithms to optimize the design and then map the components.This is shown in the below figures

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165855832-8d806d27-80fc-4a1c-9842-926a2122b389.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165855703-5428b6fe-9955-439b-9df9-bcc9e0050bc3.png" width="500"/>
</p>

<a name = "sub-sub-heading2b"/> 

####  Elobarated design 
Using the show command in the yosys tool we can see the elaborated design as shown in the figure below.This is done after creating the netlist using the abc YOSYS command  In this techology library 2X1 MUX is available so the synthasizer has direclty reaslized the design as shown below using MUX 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165857904-89881993-561e-4b1e-b9ac-8683b93f708c.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165857827-85fe56ce-ed69-42ff-a26f-ce20e2e7ab8b.png" width="500"/>
</p>

<a name = "sub-sub-heading2b"/> 

####  Visualising the generated  Netlist

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165859445-9e8996ba-7d92-4ac3-9a12-7f7242bc523e.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165859732-02bc54bd-4bd1-472a-a285-46d218338e58.png" width="500"/>
</p>

<a name="heading2"/>

## Day 2 : Timing libs , hierarchical vs flat synthesis and efficient flop coding styles


<a name="sub-heading3"/>

### Introduction to dot Lib

In this session we review what is present in the .lib file of SKY130 technology. We Analyse what are the various things that are present in the .lib file

<a name = "sub-sub-heading3"/> 

#### dot Lib Part 1 :
The SKY130 library .lib file contains the information regarding the corners, technology, delay models , units of time voltage and power . Various information regarding the cells present in the library , the power the cell consumes, the delay models of vaious gates  will be present in technology library

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165952369-8cf40fcd-5125-4190-9186-f96c9ee3e067.png" width="500"/>
  </p>

<a name = "sub-sub-heading3a"/> 

#### dot Lib Part 2  :
The discussion continues on more detailed information about the SKY130 standard cell PDK. The instructor took examples of the various AND gates and its versions,, showed the behavioural models of the standard cells present and  comparisions of the same gate with different area and power versions. All of this is indicated int he below figures 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165956648-dac4ed45-74be-41a9-b358-599554f6194e.png" width="500"/>
  </p>
  <img src="https://user-images.githubusercontent.com/64180927/165957174-4d0264c1-3281-44e9-a2dd-ad0b9204670a.png" width="500"/>

<a name = "sub-sub-heading3a"/>
