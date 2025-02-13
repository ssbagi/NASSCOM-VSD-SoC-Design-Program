# DAY 4

In Day3 we designed our own Custom Cell from Circuit to Layout design of Inverter. In Magic tool the layout of Inverter was developed. We extracted the parasitics of the Inverter and dumped into spice file. 

## Why ?
The reason is sometimes we do custom cell or group the standard cell and make a logic out of it. During Technology Mapping stage i.e., mapping logic to Standard cells. That is Logic Synthesis and Physical Synthesis step we tend to include the custom designed cell and its layout (FRAM) into our design. Then we proceed further with our Physical Design flow. 

## LAB Work
When we open the pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd. We open the tracks.info file. For this skylane130A the technology node is 130nm and the Fab gives 6 Metal Layers i.e., li1, met1, met2, met3, met4 and met5. So, during routing stage the tool using these metal tracks for routing. 

To explain or understand the concept for example : 
met1 X 0.17 0.34
met1 Y 0.17 0.34

The Metal1 track has multiple lines in Horizontal and Vertical layers in chip. The pitch(distance between the two met1 layers in Horizontal and Vertical direction) is 0.34. 

In below snippet it has offset and pitch values. Horizontal track is X and Vertical track Y. 
![image](https://github.com/user-attachments/assets/4d38c0e1-95c1-4d57-97a0-ae1103e7769e)

Now using the li1 information and chnaging the grid information.
![image](https://github.com/user-attachments/assets/ad4a2e0a-d67c-4533-ba65-5723b5f73660)








