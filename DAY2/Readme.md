**DAY1**



As part of the Lab session we are using the OpenLane tools for doing Chip design from RTL to GDSII flow. 

Image : 
![image](https://github.com/user-attachments/assets/721afbca-51f4-4e04-97c4-636b4fa2e463)

As part of the lab introduction : 

In the Process Design Kits (PDKs) the sky130A folder contains the libs.refs and lib.techs.
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


The libs.tech is the tools folder
![image](https://github.com/user-attachments/assets/c8924444-b4a1-42e7-9404-9af0d81858d2)

![Openlane_Tools](https://github.com/user-attachments/assets/31e8e2a7-e907-452f-969c-e37a21a54ed7)





