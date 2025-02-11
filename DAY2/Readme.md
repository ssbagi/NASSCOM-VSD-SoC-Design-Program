# Physical Design Flow
The Physical design flow is as follows : 

![image](https://github.com/user-attachments/assets/2b6d4618-7418-4636-8efe-57efefc5c1bb)


Most of the Chip design falls into following categories as shown in below Flow diagram. Majority of the Semiconductor comapines target for ASIC's based and in that Standard cell based Methodology. The target based methodology is Standard Cell Based becuase to reduce the design time, reduce NRE (Non Recurring Engineering) cost, reduce the TAT (Turn around time) and faster Time to Market. Faster and Efficient delivery of the chips to customer. The Lead time for the chips will be around 18 months to 24 months. Hence, Majority of the Semiconductor companies go for Standard cell based approach. 

```mermaid
graph TD;
    A[ASIC]-->B[Full Custom;]
    A[ASIC]-->C[Semi Custom];
    A[ASIC]-->D[Programmable];
    C[Semi Custom]-->F[Cell Based];
    C[Semi Custom]-->E[Standard Cell Based];
```

# Standard Cell Based Approach
In this approach majority of the standard cells are defined and delievered by the Foundaries (TSMC, Samsung, Intel, Global Foundries, Micron, SKHynix and many more). They deliver the standard cells because to save time, money and reduce risk by using a predesigned, pretested and precharacterized. The Foundry are responsible for design of the cell library and fabricate all layers of ASIC for each design. 

In Standard cell we have following categories : 
- Channeled Gate Array.
- Channel less Gate Array.
- Structured Gate Array.

Based on the applications the suitable one will be choosen. 



# Floorplan

Goals of Floor Planning
```
- Define Core and Die Area of the chip
- Placement of Physical cells.
- The overall cell is defined including cell size, supply network.
- Arrange the blocks/IP's as flexible and fixed on the chip.
- Decide the location of the I/O's pads.
- Decide the location and number of Power pads.
- Decide the Power Distribution Network (PDN) : Place the VDD and VSS Power rails alternatively in Horizontal and Vertical Metal layers.
- Decide the Location and Type of Clock Distribution.
- Utilization percentage : 80 to 85% at end of the Physical design.
```

Guidelines for a Good Floorplan

![image](https://github.com/user-attachments/assets/6ad4dbfc-8907-492e-802f-a802594feac5)


In below snippet we can see the standard rows where the standard cells get placed in these rows. 

![image](https://github.com/user-attachments/assets/d6118e00-e1c0-46fa-b765-b9af0bc770c2)

## Physical Synthesis 
![image](https://github.com/user-attachments/assets/26e75c3c-92ab-4e6e-bee1-6e3830f9d8dd)

- 𝑈𝑡𝑖𝑙𝑖𝑧𝑎𝑡𝑖𝑜𝑛 𝐹𝑎𝑐𝑡𝑜𝑟 =  ((𝐴𝑟𝑒𝑎 𝑂𝑐𝑐𝑢𝑝𝑖𝑒𝑑 𝑏𝑦 𝑁𝑒𝑡𝑙𝑖𝑠𝑡))/((𝑇𝑜𝑡𝑎𝑙 𝐴𝑟𝑒𝑎 𝑜𝑓 𝑡ℎ𝑒 𝑐𝑜𝑟𝑒) )
- 𝐴𝑠𝑝𝑒𝑐𝑡 𝑅𝑎𝑡𝑖𝑜 =  (( 𝐻𝑒𝑖𝑔ℎ𝑡))/((𝑊𝑖𝑑𝑡ℎ) )

## Preplaced Cells
These are Macros, IP's, Memory cells are part of complex logic. 

## Physical Cells
- TIE Cells
- TAP Cells
- Spacer Cells
- Feedthrough Cells
- Power Cells
- Decap Cells
- Boundary/End cap Cells

Link : https://www.physicaldesign4u.com/2019/12/physical-only-cells.html

Defining the Blockage for not placing the cells in those defined region. 

# LAB WORK
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


## Placement 
The process of arraging circuit components on a layout surface. The input are Set of fixed modules, netlist. The output is best position for each module based on the cost functions.

Optimize of the placement

```
- The cost function include wire length, wire routability, hotspots, performance, I/O pads.
- Arrange all the Standard cells within in the chip.
- Minimize the total estimated interconnect length.
- Meet the timing requirements for critical nets.
- Minimize the interconnect congestion.
```

![image](https://github.com/user-attachments/assets/9f7cf4e3-095a-4268-a8ce-929ff8e31d7a)

![image](https://github.com/user-attachments/assets/c988808f-6cf8-4d1e-bf36-ba2b18f49fb2)

![image](https://github.com/user-attachments/assets/34de1ff2-c0e0-474f-ab99-f91db720f03a)

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

Placement of the Standard cells in Standard rows

![image](https://github.com/user-attachments/assets/899f8bce-75cd-4a48-879b-68402bfbf91b)

## Cell Design Flow

![image](https://github.com/user-attachments/assets/4a64127b-f326-4c8e-8ae2-5beb4832c06b)

The CDL(Circuit Descrption language)  

![image](https://github.com/user-attachments/assets/c42a4efc-ebfe-481e-86ce-62bf16f9bd1a)

### Characterization Flow

![image](https://github.com/user-attachments/assets/7a93b3df-9c62-4761-82ef-52794bcf01bd)

![image](https://github.com/user-attachments/assets/dccb93bd-3a94-41c7-8b3b-6684a3fa68f8)












  


