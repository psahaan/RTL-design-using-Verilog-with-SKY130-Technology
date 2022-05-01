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
     + [dot Lib Part 2&3 : ](#sub-sub-heading3a)  
   * [ Hierarchical vs Flat synthesis ](#sub-heading3a)
      + [Hierarchical : ](#sub-sub-heading4)
      + [ Flat : ](#sub-sub-heading4a)
      + [ Submodule level synthesis   : ](#sub-sub-heading4a)
    * [ Various Flop Coding styles and Optimization ](#sub-heading3b) 
      + [Why Flops are required ](#sub-sub-heading5)
      + [ Different types of Flops and their Coding Styles ](#sub-sub-heading5a)
      + [ Interesting Optimizations Part 1 & 2  ](#sub-sub-heading5b) 
  - [Day 3 : Combinational And Sequential Optimizations](#heading3) 
    * [ Introduction to optimizations](#sub-heading4)
      + [ Subpart  Part 1 ,2, 3  ](#sub-sub-heading6)
    * [Combinational Logic Optimizations](#sub-sub-heading6a) 
    * [Sequential  Logic Optimizations](#sub-sub-heading6b)  
    * [Sequential  Logic Optimizations for unused ports ](#sub-sub-heading6c)   
 - [Day 4 : GLS,blocking vs non-blocking , Synthesis Simulation Mismatches ](#heading4)
   * [ Introduction to optimizations](#sub-heading4)


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

#### dot Lib Part 2 & 3  :
The discussion continues on more detailed information about the SKY130 standard cell PDK. The instructor took examples of the various AND gates and its versions, showed the behavioural models of the standard cells present and  comparisions of the same gate with different area and power versions.lib files also contains the information regarding what power is consumes and what area it has for different input combinations. All of this is indicated int he below figures 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165956648-dac4ed45-74be-41a9-b358-599554f6194e.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165957174-4d0264c1-3281-44e9-a2dd-ad0b9204670a.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165957660-1ace896c-7274-4360-bb1a-06d2b2ed2b07.png" width="500"/>
  </p>
  
<a name = "sub-heading3a"/>

###  Hierarchical vs Flat synthesis 

<a name = "sub-sub-heading4"/>

####  Hierarchical 

In this session we start with reviewing a verilog code called  multiple_modules as shown below . The main point here is that after synthesizing the architecture below the synthesized design contains sub-modules instead of discrete components. This is due to Hierarchical Synthesis .The netlist generated is also show below contains connections between sub-modules .Also attached is the netlist that is generated after synthesis 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165986994-d7208fcd-087c-4e2d-b40c-27af681154d1.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165989866-f549c9bf-8297-4434-8fc1-c9d0e8269871.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/165990491-8ad41ee8-f8cd-460a-9915-8400a4a2733d.png" width="1000"/>
  </p>

<a name = "sub-sub-heading4a"/>

####  Flat synthesis 
Now we use flattening using flatten command   to get the sysnthesized command to gate level instead of submodule level .After doing this we get something called flattened netlist instead of hierarchy netlist. This process is show below 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/165996518-d9bda6e6-aefa-4e08-946b-49ca52e3e1d6.png"/>
  <img src="https://user-images.githubusercontent.com/64180927/165996946-4381adc3-0f5c-4c80-834c-9311fbd67042.png"/>

  </p>

<a name = "sub-sub-heading4b"/>

####  Submodule level synthesis 

Used when multiple instantiation of same module or we want to do divide and conquer approach , so when design is very  massive , we will give one portion by one portion.

![39](https://user-images.githubusercontent.com/64180927/166003572-22faa3e4-5e56-43b3-a574-21237ba71286.png)

<a name = "sub-heading3b"/>

### Various Flop Coding styles and Optimization  

<a name = "sub-sub-heading5"/>

#### Why Flops are required  
To avoid Glitches that are caused by the combinational circuits and as a storage elements we need flops  

<a name = "sub-sub-heading5a"/>

#### Different types of Flops and their Coding Styles 

Here we find various coding styles of Flops as shown below , Synchronous Reset and Asynchronous Reset . Here the instructor also discussed about how various D Flip flops area synthesized using yosys 

<p float="left">
  <img src="https://user-images.githubusercontent.com/64180927/166016996-d9f8268e-7575-4329-a0cd-8f7928d5da73.png"/>
  <img src="https://user-images.githubusercontent.com/64180927/166063546-65dd4311-d566-4cfb-8034-17e482af8d98.png"/>
  <img src="https://user-images.githubusercontent.com/64180927/166063551-b9820aeb-7c5c-4a80-a8fb-a54aa885579e.png"/>
  <img src="https://user-images.githubusercontent.com/64180927/166063556-3721df1f-a4e1-4106-b46b-ad77f2a4c140.png"/>
 
  </p>
 
![synthesized design](https://user-images.githubusercontent.com/64180927/166063571-5e9fea06-50a6-40f2-9fcf-717730c88e69.png)
![synthesized design asynchronous set](https://user-images.githubusercontent.com/64180927/166063584-eaa0e64a-ffb2-4d03-a3cd-71f1123457c7.png)
![syncres_reset_synthesized design](https://user-images.githubusercontent.com/64180927/166063591-80e66fa9-411b-4904-8739-4f13bf6f2caa.png)

<a name = "sub-sub-heading5b"/> 

####  Interesting Optimizations Part 1 & 2 
Some circuits like multiplications by 2 and 9 do not actually need multipliers , this can be done very easily as shown in below circuits 
![generated netlist for mul2](https://user-images.githubusercontent.com/64180927/166144198-698ae4aa-1261-412e-8462-090657864708.png)
![multiplier by 2 synthesis](https://user-images.githubusercontent.com/64180927/166144205-9b491b6f-b943-4972-8101-b9efa5a9b540.png)
![net_list_for_multiply_by 9](https://user-images.githubusercontent.com/64180927/166144209-31ba3425-f09a-4033-84a2-6807c2645cbd.png)
![multiplier by 9 synthesized design](https://user-images.githubusercontent.com/64180927/166144211-ba4755bb-ed62-48bd-be42-a9f4df7998cb.png)


<a name = "heading3"/>

## Day 3  :  Combinational And Sequential Optimizations

<a name = "sub-heading4"/>

### Introduction to optimizations 

<a name = "sub-sub-heading6"/> 

#### Subpart 1,2,3  

In this module we are introduced to basic optimization schemes for both combinational and sequential circuits, some of them are constant logic optimization , boolean logic optimization in case of combinational circuits  and sequantial constant optimization in case of sequential circuits. Other important optimization like cloning , retiming were also discussed.


<a name = "sub-sub-heading6a"/> 

### Combinational Logic Optimizations 

Some logic with with multiplexers for which  some of the inputs of the multiplexers is tied to zero need not need  a mux they just need an AND gate , this kind of optimizations are very useful to reduce the logic , these are defined as shown below  


![13](https://user-images.githubusercontent.com/64180927/166145029-84c4abbf-5759-4595-8085-e3df6b7126d4.png)

So after running the synthesis in yosys synthesis tool as expected we will get the result as shown below 

![14](https://user-images.githubusercontent.com/64180927/166145111-64d3b13f-1385-4499-92c0-4031cdd5c2fc.png)


<a name = "sub-sub-heading6b"/> 

### Sequential  Logic Optimizations 

Similarly in case of Sequential Logic Circuits like DFF ,( not in all the cases ) but in some cases when for any combination of inputs and resets if the output is fixed we do not need any logic for that in those cases the synthasized logic is very simplified as shown below , for example there is a case when the output of the DFF is always one whether it is reset or D so in that case the synthesized design is as shown below 

![18](https://user-images.githubusercontent.com/64180927/166145330-f9d33fab-9911-484f-a19f-9c6f308915a9.png)


<a name = "sub-sub-heading6c"/> 

### Sequential  Logic Optimizations for unused ports 

Outputs not having a direct roule in determining the primary outputs , all those outputs are optimised by the synthesizer ,For example if we take a  three bit counter and take only the LSB output is playing the role in determining the final output , then the other 2 outputs of the counter are optimized , this is shown in figures below , we generally expect 3 flops in case of 3 bit counter , but if we only take the LSB output of the three bit counter the synthesis result will give only one counter , the results after synthesis are shown below 

<p float="left">
 
  <img src="https://user-images.githubusercontent.com/64180927/166145749-7b9bc0d1-7b5e-422b-bcbe-a49e553be9d1.png" width="500"/>
  <img src="https://user-images.githubusercontent.com/64180927/166145795-0e508394-8aa6-46fe-b5c0-cfc5066a28f2.png" width="500"/>
 
  </p>

And if all the 3 outputs are used in determining the primary outputs then 3 Flops are generated unlike the above case , the synthesized design is as shown below 

<p float="left">
 
  <img src="https://user-images.githubusercontent.com/64180927/166145902-5acfab76-2e2a-4030-b9cc-250ab427f610.png" width="500"/>
 
  </p>

<a name = "heading4"/>

# GLS,blocking vs non-blocking , Synthesis Simulation Mismatches 

Gatel Level Simulation is necessary to verify whether the synthesized netlist matches the RTL simulation done before synthesis and to check if there is any synthesis and simulation mismathes are present. The flow for doing the GLS is as shown below by the instructor : 


<p float="left">
 
  <img src="https://user-images.githubusercontent.com/64180927/166147123-11c33e1c-6fe7-4428-ad52-ffa31e928bdf.png" />
 
  </p>

