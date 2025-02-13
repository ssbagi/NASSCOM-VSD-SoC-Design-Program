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

Now starting once again the synthesis step. Now below in merged lef section you can see we have included the new inverter cell.
![image](https://github.com/user-attachments/assets/daad13c0-3802-4b9d-b4e0-6684be2b2de5)

Now we see our custom inverter cell is included in total list of cells. The count is 1554. 
![image](https://github.com/user-attachments/assets/da8a425b-ff46-485f-b02a-23af7aaebabe)

Cell Count Summary : 
![image](https://github.com/user-attachments/assets/c691a2f8-eca6-44fe-8664-bea62c156684)

After Modying the parameters : 

![image](https://github.com/user-attachments/assets/d424e8ba-b29c-4083-a95a-2f3b6de575bf)

![image](https://github.com/user-attachments/assets/49949561-02de-4679-9419-e04b2e77b2e5)















