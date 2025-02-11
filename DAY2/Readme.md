# Introduction
In the Initial videos gives a Overview from the PCB Board to Chip. Then we zoom inisde chip we see the basic SoC Blocks (Multiple IP Blocks and HM blocks), GPIO's, Package, I/O Pads. The core and die section of the chip. 

PCB Board : 
![image](https://github.com/user-attachments/assets/8a993c2a-8282-4995-8df2-0095c55130a4)

Inside the Microcontroller chip:
![image](https://github.com/user-attachments/assets/dc0e0cfa-4d6f-4003-a3fe-b243c8cc2c32)

![image](https://github.com/user-attachments/assets/c28de1c5-ebc4-4c4d-81bf-307c8b3e9c01)

![image](https://github.com/user-attachments/assets/1b4c7c29-71ca-4864-ab74-c59dfad12b75)

An Introduction to Instruction Set Architecture (ISA). We have multiple ISA avaialble : x86, ARM, RISC-V and Power PC. We are using RISC-V ISA since its Open Source. The ISA plays an important role in designing the chip. The codes written in high level language is converted to assembly and then to binary which follows to specific ISA of that hardware.

Basic Mapping from Applications to Hardware. Explaining about the stack. 
From : 
![image](https://github.com/user-attachments/assets/5c39b432-4b7f-4b75-a7d2-c2b0b32f4763)

To :
![image](https://github.com/user-attachments/assets/6bb18f37-0f21-4cea-8bac-afdfd08741f8)

# OpenLane Tool Introduction
As part of the Lab session we are using the OpenLane tools for doing Chip design from RTL to GDSII flow. 
 
![image](https://github.com/user-attachments/assets/721afbca-51f4-4e04-97c4-636b4fa2e463)

# VLSI Flow 
The Standard and basic VLSI flow for Chip design.

![image](https://github.com/user-attachments/assets/c36058e1-37bc-4bbb-865d-7d3f98f3dc67)


# LAB Session :

As part of the lab introduction : 

In the Process Design Kits (PDKs) the sky130A folder contains the libs.refs and lib.techs.

## libs.ref
The libs.ref contains the different process folders. In each of these process we have the library (timing corners) , lef files, spice files, mag has the cells shape, the technology lef, the verilog folder has custom defined cell definition using primitive verilog syntax. 

![image](https://github.com/user-attachments/assets/b5198ae1-22b7-4485-b9fd-968a70851651)
![image](https://github.com/user-attachments/assets/2746b90e-6843-44f7-be7b-fc1b2b71f547)

The lib folder contains the corners with PVT specified. Process Voltgae and Temprature defined. 
![image](https://github.com/user-attachments/assets/6b516238-9730-48d4-9365-89bbfdf0590c)

As an example if you go inside the directory and open the file you will see the standard cells listing. Each cell with properties defined leakage power, area, cap for each pin, rise, fall, max transition for each pin of the cell.

![image](https://github.com/user-attachments/assets/383434b5-eb07-43b5-b63e-264d42d58f4d)

![image](https://github.com/user-attachments/assets/ac36074c-4ac7-443c-a3ce-026ba0ce8c55)

![image](https://github.com/user-attachments/assets/98ddae50-bb5b-466a-adba-5ca68390c474)

The spice folder has the spice definitions for the standard cells. We can use these models when doing spice simulation or during SPEF extraction these simulation are carried out we collect that respective data.

![image](https://github.com/user-attachments/assets/976d6b96-318d-40d4-8ebf-ec1b2ae10ba7)

![image](https://github.com/user-attachments/assets/2f512f3f-6f44-47d8-b629-98d85a94888a)

In the maglef folder has definition of the technology lef details. The shape for nwell, pwell, metals, labels and GSD file.

![image](https://github.com/user-attachments/assets/84d67c13-227b-4313-9ce7-722ae8dd81b7)

The lef directory has standard cell shape definition for each pin, total shape of the cell. During placement stage the cells and these shapes gets populated on the Standad row core section of the chip. 

![image](https://github.com/user-attachments/assets/97762480-af30-48fd-af3c-e0c8d581cba7)

In the cdl folder these contains the definitions of the standard cell w, l, mult, sa and Perimeter. This is same as spice syntax.

![image](https://github.com/user-attachments/assets/3ca46585-1307-4796-a757-cb2f0aae0881)

In the verilog folder we see the primitive definition of the standard cell. Whenever there is technolog mapping or netlist is getting generated we are going to use replace our logic modules with these standard cells definition. 

![image](https://github.com/user-attachments/assets/513fbd47-510d-4340-9717-5f2fae3bd869)
![image](https://github.com/user-attachments/assets/e4928df4-f979-4c52-863e-55fa6dbc14a4)

## libs.tech

The libs.tech is the tools folder
![image](https://github.com/user-attachments/assets/c8924444-b4a1-42e7-9404-9af0d81858d2)

![Openlane_Tools](https://github.com/user-attachments/assets/31e8e2a7-e907-452f-969c-e37a21a54ed7)

## Hands On

### Step 1 : 

```
Command Used :
- docker
- package required openelane 0.9
```

![image](https://github.com/user-attachments/assets/455f068b-f0eb-4c30-9bcd-0acd290d60c5)



config.tcl
![image](https://github.com/user-attachments/assets/60f54bd9-72d0-47db-8897-f02103cbf3d8)

The files sky130A_<>.tcl these have highest priority or override the settings to hte simulation. 
![image](https://github.com/user-attachments/assets/3c5ff9e4-ae46-4877-8a9b-abfe1be59396)

```
prep -design picorv32a
```
When above command is ran you can see the config.tcl used for configuration, PDK's root directory, Standard cell library, LEF files and Metal layers (Only 6 layers are avialble). Then Merging lef (Cell level lef and technology level lef). 

![image](https://github.com/user-attachments/assets/48f57d8a-92d7-47a5-a5d2-8e0b4b59579b)

The runs directory creation taking palce : We can see the timestamp also. 
![image](https://github.com/user-attachments/assets/ad7c2b95-ee30-4aca-9926-b1e68230de87)

Now going inside tmp directory : 
![image](https://github.com/user-attachments/assets/ca7c1984-6c26-4e60-b549-ce81db3ba1b8)

In the Results Directory we have for each stage separate direcrtory creation and results avilable inside that. 
![image](https://github.com/user-attachments/assets/cb8469af-f6d7-4f5d-8722-58255f5bfbbc)

Similarly we have reports directory also same as results.
![image](https://github.com/user-attachments/assets/dc04e639-ccaf-4a9c-b657-7106c039c313)

The config.tcl file present in the runs directory give the list of commands used for the Simulation. 
![image](https://github.com/user-attachments/assets/94e71dc3-efbc-45f4-948c-623d4060d562)

## Synthesis 

The Synthesis stage generally takes input of the design files (Verilog files), Constraints and Standard cell library (.lib) to generate the Equivalent Logic Circuit. 

![image](https://github.com/user-attachments/assets/60efdfa2-217d-44af-a4fd-abf3c2521057)

![image](https://github.com/user-attachments/assets/44ef1fad-70ad-4b77-9fdd-cf5e9974817d)

Command used for yosys tool : 
```
run_synthesis
```

![image](https://github.com/user-attachments/assets/4ac7a7c9-adfe-4a32-86d8-2ac2942f3d3d)

Results after Synthesis Step is as follows : 

![image](https://github.com/user-attachments/assets/a20b93e3-89b5-46ef-9dda-94c028d4904e)

The Chip area of the chip is 147712.918400.

![image](https://github.com/user-attachments/assets/303b1512-21c4-43f4-a2e5-2d638bd0171a)


# FLOP RATIO

![image](https://github.com/user-attachments/assets/d3a9dff9-4733-4f4d-8ec3-e523f1aa8af9)

The count of D-FF is 1613. 
![image](https://github.com/user-attachments/assets/f7436662-5992-4a4b-88c4-1182a6e88827)

The synthesis netlist generated file as shown below : 
![image](https://github.com/user-attachments/assets/f703d861-0859-4e9d-a6e3-f70464be50d7)

The synthesis reports directory : 
![image](https://github.com/user-attachments/assets/eec868f0-a68a-4a4b-bbbf-8586c8b27599)











