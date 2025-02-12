# NASSCOM-VSD-SoC-Design-Program
As part of the Workshop VSD SoC Design Course. 

# DAY 1 : LAB Work
As part of the lab introduction : 

In the Process Design Kits (PDKs) the sky130A folder contains the libs.refs and lib.techs.

## libs.ref
The libs.ref contains the different process folders. In each of these process we have the library (timing corners) , lef files, spice files, mag has the cells shape, the technology lef, the verilog folder has custom defined cell definition using primitive verilog syntax. 

![image](https://github.com/user-attachments/assets/b5198ae1-22b7-4485-b9fd-968a70851651)
![image](https://github.com/user-attachments/assets/2746b90e-6843-44f7-be7b-fc1b2b71f547)

## libs.tech

The libs.tech is the tools folder
![image](https://github.com/user-attachments/assets/c8924444-b4a1-42e7-9404-9af0d81858d2)

![Openlane_Tools](https://github.com/user-attachments/assets/31e8e2a7-e907-452f-969c-e37a21a54ed7)

## Hands On

### Step 1 : 

```
Command Used :
- docker
- ./flow.tcl -interactive
- package require openlane 0.9
```

![image](https://github.com/user-attachments/assets/455f068b-f0eb-4c30-9bcd-0acd290d60c5)

```
prep -design picorv32a
```
When above command is ran you can see the config.tcl used for configuration, PDK's root directory, Standard cell library, LEF files and Metal layers (Only 6 layers are avialble). Then Merging lef (Cell level lef and technology level lef). 

![image](https://github.com/user-attachments/assets/48f57d8a-92d7-47a5-a5d2-8e0b4b59579b)

## Synthesis 

The Synthesis stage generally takes input of the design files (Verilog files), Constraints and Standard cell library (.lib) to generate the Equivalent Logic Circuit. 

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


# DAY 2 : LAB WORK
The variables defined for Floorplanning are as shown below : 

![image](https://github.com/user-attachments/assets/6bfc66d3-8ca5-4a43-800b-af128258fee0)

## Floorplan Tcl Script Configuration
The floorplan tcl script used for configuring the simulation. 
![image](https://github.com/user-attachments/assets/d1f55857-dbf4-4d3d-b843-fc4357228485)

```
run_floorplan
```

![image](https://github.com/user-attachments/assets/ffa17e98-b11c-496f-ab06-cefd0ebf979b)

Opening the Magic Tool. The cirrent directory is in <TIMESTAMP>/results/floorplan
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/skylane130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def
```

![image](https://github.com/user-attachments/assets/4cc7ae3c-7bf3-4355-8891-88df5caecc2e)

![image](https://github.com/user-attachments/assets/3c1a6a6e-7079-4277-a866-04bd582b4dda)


```
s    - Used to select the object.
v    - center the Die.
what - dispalys the details of the object.
```

In below section shows the object of pins are routed in metal2.
![image](https://github.com/user-attachments/assets/c4f2e828-bc39-4f8d-9295-d60f50eb0b38)

All the logic blocks standard cells are placed in left side corner.
![image](https://github.com/user-attachments/assets/04abd242-3c33-4ebe-aa76-e6cf9dd0f827)

```
run_placement
```

![image](https://github.com/user-attachments/assets/643f2e98-d358-4551-9752-3f5f7b6c5705)

After the command ran : 

![image](https://github.com/user-attachments/assets/cc1e3e66-34d0-4a41-8769-f0776d55e93e)

![image](https://github.com/user-attachments/assets/67ec6809-6107-4a9b-9474-2299e70c2327)

```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/skylane130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def
```

Opening the Chip after run_placement stage

![image](https://github.com/user-attachments/assets/7b08b12b-c925-4c16-9d3a-0c1e3b3b0cd8)

After every run the screenshot of the result is takenand stored. The View of chip afer this step done is as follws : 

/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-02_14-38/results/placement/picorv32a.placement.def.png


Placement of the Standard cells in Standard rows

![image](https://github.com/user-attachments/assets/899f8bce-75cd-4a48-879b-68402bfbf91b)





# Day 1
Link : https://github.com/ssbagi/NASSCOM-VSD-SoC-Design-Program/blob/main/DAY1/Readme.md

# Day 2
Link : https://github.com/ssbagi/NASSCOM-VSD-SoC-Design-Program/blob/main/DAY2/Readme.md

# Day 3
Link : https://github.com/ssbagi/NASSCOM-VSD-SoC-Design-Program/blob/main/DAY3/Readme.md

# Day 4
Link : https://github.com/ssbagi/NASSCOM-VSD-SoC-Design-Program/blob/main/DAY4/Readme.md

# Day 5
Link : https://github.com/ssbagi/NASSCOM-VSD-SoC-Design-Program/blob/main/DAY5/Readme.md


