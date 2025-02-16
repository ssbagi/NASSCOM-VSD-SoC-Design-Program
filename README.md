![image](https://github.com/user-attachments/assets/85858bab-1623-45d8-bd49-ddcf886bee8f)# NASSCOM-VSD-SoC-Design-Program
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


# DAY3 LAB WORK

## Magic Layout and NGSPICE Characterziation

![image](https://github.com/user-attachments/assets/6af93eab-db17-44dd-aa5d-0e60a65b5ba2)

```
magic -T sky130A.tech sky130_inv.mag &
```

Now we see the Layout of the Inverter. We see the following layers :

```
p-well
n-well
Gate of pmos and nmos are connected to Input pin.
Drain of pmos connected and Drain of nmos are shorted and connected to Output pin.
Source of pmos connected to VDD
Source of nmos connected to VGND
Polysilicon : Red line
```

![image](https://github.com/user-attachments/assets/026d11d5-313a-444e-9cb0-c036c8788d0e)

By selecting usin keyboard key s and typing what in the console we see selected one is polysilicon layer. Connecting Gate of both nmos and pmos.
![image](https://github.com/user-attachments/assets/24419a53-6b2c-4045-8646-b9938b4dee12)

Similar for n-well.
![image](https://github.com/user-attachments/assets/0156dcf0-eedf-4ac7-8b95-effba8978091)

The Technology LEF - It contains information about avialable metal layer via information DRC's of paticular technology used by placer and router etc.

## Standard Cell layout design in Magic
Extracting the details form the layout, parasitics from the cell. 

```
extract all
ext2spice cthresh 0 rthresh 0
ext2spice
```
![image](https://github.com/user-attachments/assets/5f871793-d38d-4858-90fa-fa7b48c95ffc)

![image](https://github.com/user-attachments/assets/edc27b41-e740-4393-a261-e5ad852d2aea)

After opening the extracted spice file.
![image](https://github.com/user-attachments/assets/7604f970-e8de-45cd-807e-07461b4414a3)

Spice file sky130_inv.spice contents. Adding the pmos, nmos model files, Pulse and doing Transient analysis on the inverter.
![image](https://github.com/user-attachments/assets/8bab2ab5-9fe2-4b01-bd09-eb9554d97844)

## NGSPICE 
Loading the skylane130_inv.spice file in ngspice tool.
![image](https://github.com/user-attachments/assets/f4ba2453-d889-4f76-bc40-8a9837bda055)

The Input and Output Waveforms of Inverter
![image](https://github.com/user-attachments/assets/48a0882f-304f-4dc9-81d9-4b477773c036)

![image](https://github.com/user-attachments/assets/cd2dbfc8-c50d-4181-8923-9fea81dc239d)

The basic tr Rise time calculation. 20% to 80% value changes. 
![image](https://github.com/user-attachments/assets/7f60941c-3d6f-448c-854d-c87d6db03797)

The basic tpd Propogation delay. 50% of Output to 50% of input.
![image](https://github.com/user-attachments/assets/5a814374-478c-46f3-a2df-b9e1a060d9cd)

The basic tf Fall time calculation. 80% to 20% value changes.
![image](https://github.com/user-attachments/assets/45a353e0-befe-4438-b3a4-1e2653a5cfea)

## DRC Error



# DAY 4

In Day3 we designed our own Custom Cell from Circuit to Layout design of Inverter. In Magic tool the layout of Inverter was developed. We extracted the parasitics of the Inverter and dumped into spice file. 

## Why ?
The reason is sometimes we do custom cell or group the standard cell and make a logic out of it. During Technology Mapping stage i.e., mapping logic to Standard cells. That is Logic Synthesis and Physical Synthesis step we tend to include the custom designed cell and its layout (FRAM) into our design. Then we proceed further with our Physical Design flow. 

## LAB Work
When we open the pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd. We open the tracks.info file. For this skylane130A the technology node is 130nm and the Fab gives 6 Metal Layers i.e., li1, met1, met2, met3, met4 and met5. So, during routing stage the tool using these metal tracks for routing. 

To explain or understand the concept for example : 
- met1 X 0.17 0.34
- met1 Y 0.17 0.34

The Metal1 track has multiple lines in Horizontal and Vertical layers in chip. The pitch(distance between the two met1 layers in Horizontal and Vertical direction) is 0.34. 

In below snippet it has offset and pitch values. Horizontal track is X and Vertical track Y. 
![image](https://github.com/user-attachments/assets/4d38c0e1-95c1-4d57-97a0-ae1103e7769e)

Now using the li1 information and chnaging the grid information.
![image](https://github.com/user-attachments/assets/ad4a2e0a-d67c-4533-ba65-5723b5f73660)

Dumping the lef file of the standard cell.
![image](https://github.com/user-attachments/assets/50602810-0ea0-410f-931d-7df0de29860a)

Next step is to plug this lef file to our design. We copy the file and move to src directory.
![image](https://github.com/user-attachments/assets/d902ae67-80e9-4e05-9894-7a7ef3924ae0)

Now when we open anyone of our lib file. We see following table 

![image](https://github.com/user-attachments/assets/52ec44bf-eb3c-4496-8705-e0da637afec0)

For timing we have tr, tf and tpd. The chacterization table for each pin and the details.
![image](https://github.com/user-attachments/assets/08f67436-4534-4157-81a8-7fe87e9a973d)

![image](https://github.com/user-attachments/assets/14d36827-2a18-4060-ae96-5db5d4f95410)

For doing STA analysis we generally use the concept of Multi Mode and Multi Corner (MMMC). In our case we have
- skylane130_fd_sc_hd__typical.lib : skylane130_fd_sc_hd__tt_025C_1v80. 
- skylane130_fd_sc_hd__slow.lib  : skylane130_fd_sc_hd__ss_100C_1v60
- skylane130_fd_sc_hd__fast.lib  : skylane130_fd_sc_hd__ff_n40C_1v95

For example the skylane130_fd_sc_hd__<nmos,pmos>_<temp>_<voltage>. 

Copying all the library files to design src folder. 
![image](https://github.com/user-attachments/assets/7ee6eb07-2d51-4bcc-a851-233c97833577)

Now we have lef and timing definition library files included in this.
![image](https://github.com/user-attachments/assets/43ca6a13-4519-4054-86bb-b94a45321ca1)

Updated config.tcl file : 
![image](https://github.com/user-attachments/assets/5e3df8cb-8c70-426b-8aed-fbe35839d161)

Inclusion of Custom cell : 

![image](https://github.com/user-attachments/assets/afd02c3e-eb3c-4029-9626-c490ee2505f2)

![image](https://github.com/user-attachments/assets/031bc3c7-1cf9-4c93-9395-f92cdefc116a)

![image](https://github.com/user-attachments/assets/fb5aa944-2e80-42dc-a692-ac52c872359e)

## Synthesis of including custom cell : 

![image](https://github.com/user-attachments/assets/44cd860f-4e7a-4c54-a9c5-c7e0ad5dcf05)

![image](https://github.com/user-attachments/assets/9d1bf3eb-9391-4a59-8950-74b72d7317c9)

## Placement : 

![image](https://github.com/user-attachments/assets/ee704859-b096-4ad5-a39b-850d8d65f1b4)

![image](https://github.com/user-attachments/assets/6fc1dc7c-392d-41bc-82f6-4b2f4912f80f)

## STA Fixes : Pre-layout Fixes 

### Round 1

![image](https://github.com/user-attachments/assets/1942dd29-9f06-47a9-99c6-1ae264e69795)

### Round 2

![image](https://github.com/user-attachments/assets/9de76430-7fd2-4c46-a83d-3c5fb49fb2c5)

### Round 3

![image](https://github.com/user-attachments/assets/357f3b30-0a92-47ca-92b1-1c61faaaea94)

### Round 4

![image](https://github.com/user-attachments/assets/d77de7f0-1719-473c-bffc-53388e623942)

### NOTE 

Give feedback to Logic team to reduce as much as possible because once if you do floorplan, placement. Reduce the setup as much as possible. Next after CTS we will have setup and hold violation also. Make a note of all the fixes sent to folks and send in mail. Add commands also in the mail it becomes easy for them to take in fixes. 

Again, after Routing. The Routing is iterative process again and again it will be done. The fixes can be same(repeated) or different. Sometimes fixes are taken in and some times they are missed. Check with previous reports to newly generated ones. Make a note of all the fixes sent to PnR folks and send in mail. Add commands also in mail it becomes easy for them to take in fixes.  

![image](https://github.com/user-attachments/assets/cadd1cfe-637b-443e-9590-57d9269f4c51)

### Final Fixes

![image](https://github.com/user-attachments/assets/ed8e6846-acfa-4da6-806b-22264af4c9b7)

Next Dump Verilog file : 

![image](https://github.com/user-attachments/assets/54e63e03-2f45-4ed0-82a2-d70626513c20)

![image](https://github.com/user-attachments/assets/406bc012-c879-4623-8839-9a32f41bb2c5)

# Placement 

![image](https://github.com/user-attachments/assets/18eadf10-c2ba-45ee-be5d-c25da2e920a5)

![image](https://github.com/user-attachments/assets/1046bc84-4349-4417-9a5c-87db95eac05b)

![image](https://github.com/user-attachments/assets/41ed189d-eb98-41a6-8328-2897c77e3869)

# CTS 

In the Clock path we have separate Clk Buffer or Clk Inverter cells placed. We have X or H tree from theory in practical or in projects this will be different a little bit. Now in CTS stage onwards will have to focus on Hold time as we did for Setup time. So, many times the fixes given for setup might help or worse the Hold time if path is common. 

In below screenshot you can see the list of cell included are shown below : 

![image](https://github.com/user-attachments/assets/dcc36b75-4b07-41f2-8c37-d475f0eb6bfd)

## Why clk cells ?

Because the clk path needs to have tr = tf.  There needs not be any degradation of the signal on the clk path. 

![image](https://github.com/user-attachments/assets/bdeda28c-95ec-43de-8630-fb785272be6b)

![image](https://github.com/user-attachments/assets/3626bd38-d87f-4983-b27a-169226ef7591)

In CTS insertion of clock cells happen and new netlist is generated. 

![image](https://github.com/user-attachments/assets/512af50f-8016-40ad-875f-7a64abf46371)

































