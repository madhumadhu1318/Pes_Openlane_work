# ☑️ OPENLANE ☑️

## ABOUT THE REPOSITORY
OpenLane is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.

You can check out the documentation, including in-depth guides and reference manuals at [ReadTheDocs](https://openlane.readthedocs.io/).


![1](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/abd21a4e-c17c-4566-8e01-1af759293d0f)



 # COURSE 
<details>
<summary> DAY 1 : Insecption of open-source EDA, Openlane and sky130pdk  </summary>
<br>

# 1) Introduction to QFN-48 Package,chip,pads,core,die,and IP's and Introduction to RISC-V

- Generally an Aurdino board or an FPGA board consists of an chip or processor inside it.
- The internal veiw of chip will be as below

![2](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/49faafd4-ae04-4fc1-aa30-0a42aeb8ce1f)



![3](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/13e4e744-6856-4c97-b971-bd7565a6be91)



RISC-V is an open standard instruction set architecture based on established reduced instruction set computer principles. Unlike most other ISA designs, RISC-V is provided under royalty-free open-source licenses. 


![4](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/52c420a4-edb0-4f8f-8267-dd773d2ad9d9)






# 2) SOC Design and OpenLANE

## a) Components of open-source digital asic design**
 - Digital ASIC design, It mainly consists of
   - RTL IP's
   - EDA Tools
   - PDK Data

![5](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/d9a40659-2d69-4f96-8db7-48c02d3cc8f4)

      

  - Open source digital ASIC design

![6](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/16f9378c-de24-4883-ae4b-34566fa1b90e)


- What is PDK..?
  - Process Design Kit (PDK) Collection of files used to model a fabrication process for the EDA tools used to design an IC.
      - Process design rules : DRC,LVX,PEX
      - Device models
      - Digital standard cell Libraries
      - I/O libraries


 
## b) Simplified RTL2GDS Flow**

![7](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/a31b095c-708c-4e31-af25-f036599425e7)


         1. Synthesis
         2. Floor planning and Power planning
         3. Placement 
         4. Clock tree synthsis (CTS)
         5. Routing 
         6. Sign off



## c) Introduction to Openlane ans strivechipsets**

   #### OPENLANE was started as an open-souce flow for a true Open source Tape-out experiment,
   #### STRIVES is a family of open everything socs.

![8](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/700a23d7-6d79-4067-a944-ff56578ed7f6)


   #### Goal of Openlane asic flow is :
    - Produce a clean GDSII with no humaninterventions
         - CLEAN means 
                - No LVS voilations
                - No DRC voilations
                - Timming voilations

    - Open Lane is tunned for the skywater 130nm open PDK .
    - Open lane is containerzied which means
                - Functional out of the box 
                - Instruction to built and run natevly with flow
    - Open lane has two mode of operation 
                - Atonomous 
                - Interative


## d) Introduction to Openlane Detailed ASIC flow design


![9](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/ea74855f-0a47-47ac-957d-01342f1da0da)

   
Here's a detailed ASIC design flow using OpenLane and the associated tools and software:

**1. Synthesis:** RTL code is synthesized into a gate-level netlist, optimizing for area, power, and timing.
   - **Tools/Software**: 
     - Yosys for synthesis.
     - ABC (A System for Sequential Synthesis and Verification) for technology mapping.
     - Cell libraries specific to the target process.
     - Yosys

       
**2. Floorplanning:** Define the chip's area and arrangement of major functional blocks.
   - **Tools/Software**: 
     - OpenROAD's TritonRoute for global placement.
     - Magic for floorplan visualization.
     - Chip floor planning - Partinioning the chip die between different system building blocks and place the I/O pads.
     - Macro floor planning - Dimensions, Pin locations, rows defination.
     - Power planning - It is typically assigned with multiple VDD and VSS (Power straps, Power pads, Power rings)
    
       
**3. Placement:** Position individual gates and standard cells optimally within the predefined areas.
   - **Tools/Software**: 
     - RePLace (REctangle PLACEr) for placement.
     - Magic for placement visualization.
     - Placement is usually done in 2 steps
              - Global placement
              - Detailed placement

       
**4. Clock Tree Synthesis:** Design a clock distribution network to ensure synchronous clock signals.
   - **Tools/Software**: 
     - OpenROAD's TritonCTS for clock tree synthesis.
    
     
**5. Routing:** Establish interconnections while adhering to design rules, optimizing for signal integrity and timing.
   - **Tools/Software**: 
     - FastRoute for global and detailed routing.
     - Magic for routing visualization.


**6. Design Rule Checking (DRC):**  Verify that the layout complies with manufacturing design rules.
   - **Tools/Software**: 
     - Magic for initial DRC checks.
     - OpenROAD's TritonRoute for DRC repair.


**7. Layout Versus Schematic (LVS) Verification:** Confirm that the physical layout matches the intended functionality described at the RTL level.
   - **Tools/Software**: 
     - Netgen for LVS checks.


**8. Parasitic Extraction:** Extract parasitic capacitance and resistance values from the layout for accurate timing analysis.
   - **Tools/Software**: 
     - QFlow's SPEF extraction tool for parasitic extraction.


**9. Static Timing Analysis (STA):** Analyze timing paths to ensure setup and hold time constraints are met.
    - **Tools/Software**: 
      - OpenSTA for static timing analysis.


**10. Physical Verification:** Perform a series of checks including DRC, LVS, and electrical rule checks (ERC).
    - **Tools/Software**: 
      - Magic for DRC and LVS checks.
      - Netgen for ERC checks.


**11. GDS2 Generation:** Convert the final layout data into GDS2 format for fabrication.
    - **Tools/Software**: 
      - Magic for GDS2 generation.Here's a detailed ASIC design flow using OpenLane and the associated tools and software:



#### Synthis exporation
![10](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/7685d19b-44ed-4824-aa77-ee44a81af1bd)


#### Design exploration
![11](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/d0cc951d-023f-48d5-8e72-1483ed3e91ab)



# 3) Open- Source EDA tools

#### Openlane Directory structure in detail

   - cd Desktop/
   - cd home/tools/
   - cd openlane_working_dir/
   - ls
   - cd openlane
   - docker
   - ./flow.tcl -interactive

![12](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/54f4a77d-6bfc-44ab-bd95-33ad78c536cd)



#### Design Preparation step

    - in openlane directory
    - package require openlane 0.9
    - prep -design picorv32a

![13](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/92078eac-752d-43b2-92e6-d17f11b965e3)



#### Review files after design synthsis and run synthsis

    - run_synthesis

![14](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3d076fba-1703-4e2d-aba7-3c05f275568c)



![15](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3665e66b-190a-4787-902a-eee3cd509d5f)



   - Here the counter d flipflop is **1613**
   - The number of cells is **14876**
   - The flop ration for our design will be 1613/14876 = 0.108
   - In percentage = 10.08 %

     
#### Openlane Project Github link Discription

https://github.com/efabless/openlane

[Back to COURSE](https://github.com/madhumadhu118/Pes_Openlane_work/tree/main#course)

</details>




<details>
<summary>DAY 2 : Good floorplan vs bad floorplan and introduction to library cells </summary>
<br>


# GOOD FLOORPLAN VS BAD FLORPLAN AND INTRODUCTION TO LIBRARY CELLS

## 1) CHIP FLOOR PLANNING CONSIDERATIONS

## L1) Utilization Factor and Aspect ratio

 ![16](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/01ea862d-ce04-4f90-9137-cb29b1cd51da)


    - Defining the width and height of the core and Die
    - Consider a netlist with 2 FF and 2 gates with the connections shown below


**STEP-1** Make the gates as a Squared box 

![17](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/0c4e9454-17e5-4bfb-bf30-542e549c7c40)



**STEP-2** Find out the dimensions of the core and Die ( Dimensions of the standard cells )

![18](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3d313edf-b139-45b0-9d65-a3dac8e35287)



 #### For example 
  - Let us assume that each FF and Gates is on 1 cm breadth and 1cm height
  - Now Area of each standard cell will be will of 1 cm sq .
  - Allining tha area ocuupied the netlist in a in a single core .
  - Below the netlist will be fit into the core So it will be **100% utilization**
  - **Utilization factor** = Area occupied by the netlist / Total area ocuupied by the core.
  - where 4sq / 4sq = 1 . 
  - In this case when utilization factor = 1 , then the core is full no extra components can be added.
  - **Aspect ratoio** = Height / width , if it is 1 , it signifies that the core is square shaped.




## L2) Pre placed cells

![19](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/dcd78a1a-8a56-457b-b9e7-9d9ad06e7b42)


  - Conisder a combinational block -> Gate level diagram.
  - Seperate that gate level diagram into two blocks.
  - Consider the multiple blocks are inside a Black box Now seperate the blackbox as two differnet IP's or Modules .
  - The Arrangements of the IP's in a chip is called as **Floor planning**.
  - The IP's will have an user defined loctions and they can be placed in a chip before the placement and rouiting is done hence these are calle as **Pre placed Cells**




## L3) Decoupling Capacitors

![20](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/7ceb241a-fbfb-4099-8d80-d402bae5a65e)


  - For any signal to be considered as a Logic 0 and Logic 1, It should be within the NM range ( Either NML or NMH )
  - The area between the NML and NMH is called undefined area
  - So in order to maintain the signal to be in the NML or NMh **Decoupling capacitors** are used.
  - Decoupling capacitors are mainly used to maintain the signal are not inside the undefined area.
    



## L4) Power Planning

![21](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/10ea1644-58d7-47f6-a4fc-16b19251c8c3)

  - Insted of using individual VDD and VSS for multiple cells in a Block.
  - Suppose if there are four cells in a Block , Each cell having seperate VDD and VSS are called as **Power Planning**




## L5) Pin placement and Logical cell placement Blockage

![22](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/8bc5a0a7-547f-4540-972a-52ac2e3b48a5)

  - Here consider a 4 set of circuts with input, clk and output,
  - Considering all 4 circuits together and placing on a chip in such a way that INPUTS should be at one side and OUTPUT should be at one side which helps us to make the connections easily.
  - So this process is called as **Pin placement**
  - Making sure that non of the automated routing tool should not be placed near the i/p and o/p cells it needs to block the cells This is called as **Logical cell placement Blockage**
    

**Pin Placement**

![23](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/44840538-b028-44c3-8844-1cdd21fd52b5)


**Logical cell placement Blockage**

![24](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b152b3d2-8d85-4766-9c58-4ad1a573bf7c)






## L6) Steps to run Flopor planning using Openlane

      - These are the defalt Floorplans 
 
![25](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/c5b57062-cee9-44d7-adeb-e697c0749b59)



![26](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b13257b7-4c7b-44ce-8419-64108a03f598)



![27](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b6e1338e-b036-4258-93b3-d0b8fdf9a8a3)



## L7)

              - In the openlane shell

![28](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/7cd543b6-10fb-454b-8143-a81d7666c587)

              
              - To open the Floorplan we go to the required directory that is
                   > vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-09_15-36/results/floorplan
              - Using the ```cd``` command.
              - Then we type the command:
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

              - The following layout is displayed

![29](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/274dcaf4-4e25-47ff-8bec-3ad19090ccca)


              - We can press 's' and then 'v' to align the design to the center of the screen.

              - We can right click on the mouse and pess 'z' to zoom into a desired part.

![30](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/da1a8425-fe36-4584-8d84-2ecd249335bd)


              - We can check the details of the ports as follows
              - Hover over a port with your crosshair and press 's' on your keyboard
              - Now open the tkcon command window and type ```what```.
              - This will show you the details of the selected port.

![31](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/2cef8a3f-8d15-4a0c-b962-8e35f4869e12)

             
              - If we zoom in a little more, we can see the tap cells.
              - They are present to prevent latch up conditions which occur in the CMOS devices

![32](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/9b9a7ddc-898a-4f86-a18c-e14e281c7d1c)


              - These are the standard cells that are used in the design




## 2) LIBRARY BINDING AND PLACEMENTS


### L1) Netlist binding and initial Place Design

       - Bind netlist with physical cells 
       - Here it defines about the shape and sixe of the standard cell
       - Each cells are defined only in either rectange shape or square shape 
       - In this example, 1 refers to NOT gate, 2 refers to AND gate.   [image 1]
       - Larger the cell size 
          > It has a least resistance path
          > Performes Faster
       - Once we have a Physical veiw of all cells, It is placed on the Floorplan according to the Netlist.  [image 2]

![33](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/e30bc272-93e1-4d95-97e8-1913e2248067)



![34](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/14cac705-6ae3-4766-a76c-da87cbda046c)




### L2 and L3) Optimize placement using estimate wire length and capacitance

        - When the cells are not extactly placed on the floorplan as in the netlist, If the relevant cells are not near to i/p or o/p.
        - Then estimation of wirelength and capacitance comes in.
        - Depending on the Capacitance and how far the cells are from input and output, Some **Buffers** are added in order to reduce the Wirelength and also to get a complete signal without any             lossses of signal ( but in cost of Area which can be minimized later )
    
          
![35](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/543a4de9-2c38-49f9-977a-046b7dc461cf)



![36](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/fecf815d-dc38-4b80-97cb-a98f2670d008)



### L4) Need for libraries and characterization 

        - Library characterization and modelling depends on some steps,
        - Logic synthesis  ->  Floor planning  ->  Placement  ->  Clock Tree synthesuis ( CTS )  ->  Routing 
        - The collection of all the standard cells are placed is one area which is referred as **Library**

        
![37](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/9ecf3455-574c-4986-9c9c-a0169297b30e)




### L5) Congestion aware placement using replace
          - To view the placement we type
                   > run_placement
          - In the OpenLANE shell.

![38](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/97451e4c-529e-45e3-b5ce-c5c360714c3f)


          - This is the result displayed. As we can see the '/picorv32a.placement.def' file is read.

![39](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/ab9b5d46-5e6a-4905-b81e-6837ad84325f)


          - We move one directory up from the 'floorplan' folder using
                   > cd ../placement/

          - To view the placement design we use the command
                   > magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def

![40](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/9a99c6bb-1247-4dc1-9719-c1615805f790)

          - The above is displayed.
          - All these standard cells were present at the initial layout of the floorplan.

![41](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/4e99df22-0554-4f13-82ee-0d52a41d7168)

          - If we zoom in we can see the placement of the standard cells in the standard cell rows.




## 3) CELL DESIGN AND CHARACTERIZATION FLOW

### L1) Inputs for cell Design Flow
       - For each standard cell (AND,NOR,INVERTER,FF ect) There are different cell design flow
       - Each Cell Design Flow consists of 3 steps:
               - Inputs ( which mainly consists of PDK's [ DRC and LVs rules, Spice models, library ect] )
               - Design Steps (this mainly invovles 3 steps)
                      - Circuit Design
                      - Layout Design 
                      - Charecterization
               - Outputs ( Outputs we get here is  CDL circuit description language )
               
   #### User defined specifications
       - Cell height = The seperation between the power rail and ground rail defines the cell height.
       - Supply voltage = A certain cell should be operated at a certain supply voltage which is defined by the Top level design
       - Metal Layer = Certain Libraries van be designed on a particular Metal Layer.
       - Pin Location = Library nedds to decide on the pins and the pin location where it needs to be placed.

               
### L2) Circuit Design step
      - There are teo steps involved in circuit design:
            > Implement the Function itself
            > Modelling the PMOS and NMOS transisters in such a way that the aspect ratio should be matched.
            
      
### L3) Layout Design step
      - Implimenting the PMOS and NMOS values into layout are called Layout Design 
      - Steps involved in the layout design are:
           - Get the function implimented through the MOS transistors
           - Get a PMOS network graph and NMOS network graph
           - Obtain Euler's Path and draw a Stick Diagram
           - Convert the stick diagram into a proper Layout diagram
           - EXtract the paracetics from the layout and CHaracterize it interms of Timmings.

           
### L4) Typical Charaterization Flow
     - Steps involved in the characteriztion flow are :
           - Read in the Model Files
           - Read the extracted spice netlist
           - Define how to recongnise the behaviorur of the buffer
           - Read the subcircuits of the inverters 
           - Attach the neccessary Power source
           - Apply the stimulus
           - Provide the neccessary output capacitance
           - Provide the necessary simulation command.
           - Feed in all the 1 to 8 steps to a configuration file ( GUNA )


![42](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/a27f76f6-d0ef-4f2e-9f3c-30dadb0d1f87)


![43](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/f3d1b973-7a9e-46f9-8e42-6f396fb463c5)



![44](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/e9fe2fcd-a830-4c27-a439-f44470752fb9)



## 4) GENERAL TIMMING CHARECTERIZATION PARAMETERS

### L1) Timming Threshold definations
      - Timming Threshold Definations
          - slew_low_rise_thr
          - slew_high_rise_thr
          - slew_low_fall_thr
          - slew_high_fall_thr
          - in_rise_thr
          - in_fall_thr
          - out_rise_thr
          - out_fall_thr

![45](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/19c75bd4-da99-4a17-b880-5b3ffe579611)



![46](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/fcc57079-cef6-4bf0-9960-b4e924d7027c)



         
### L2) Propogation delay and transition time

**Propagation Delay**
The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value.
     
     - There should be no negative delay in the charecterization, This can be taken care by setting a proper threshold point.

```
    Propagation delay = time(out_fall_thr)-time(in_rise_thr)

```
![47](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/0745b0bc-9233-467c-98c9-d8261176965b)


![48](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/dd76f907-75b2-41f2-9517-b81b6555ef06)



**Transition Time**
The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

```
Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr)
```

```
Fall transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)
```

![49](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/dfabfbf4-1bd8-43ed-82a7-493369bc5808)



[Back to COURSE](https://github.com/madhumadhu1318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 3: Design library cell using magic layout and ngspice characterization </summary>
<br>

# 1) LABS FOR CMOS INVERTER NGSPICE SIMULATIONS

   ### L1) IO Placer revision
   
   ### L2) Spice deck creation for CMOS inverter
             - Create a SPICE DECK first
             - > Connectivity information about the netlist
             - > Set a component values
             - > Identify the nodes
             - > Name the nodes


![50](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/ed38e36d-3b27-4ff9-9adf-767ece976831)


             SPICE DECK = ***Model description***
                          ***Netlist Description***
                          M1 out in vdd vdd pmos w=0.375u L=0.25u
                          M2 out in 0 0 nmos w=0.375u L=0.25u
                          
                          cload out 0 10f

                          Vdd vdd 0 2.5
                          Vin in 0 2.5
                          
                          *** Simulation commands ***
                          .op
                          .dc Vin0 0 2.5 0.05

                          *** .include tsmc_0.25um_model.mod ***
                          .LIB "tsmc_0.25um_model.mod" CMOS_MODELS
                          .end
                          
                          
![51](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/00dd3e37-723f-4c12-acc0-e39fe37fbe3c)



![52](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/06a99faa-e0bd-41b7-96ba-9ef2d216e72f)

 
   
   ### L3) Spice simulation lab for cmos inverter
                  - Spice simulation for a particular specification

![53](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/30410f56-0989-4e15-9b47-902c727b2057)


![54](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b9e11fe3-81e7-45fd-a5d3-73d5e81039da)



   ### L4) Switchin threshold vm
            - The CMOS on the right side has a bigger size than the one on the left.
            - These waveforms tell us that the CMOS is a very robust device. The characteristics of the CMOS are maintained across a variety of sizes.
            - The arrow is pointing to the point where 'Vin = Vout'.

![55](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b797dfe1-4856-4cce-9113-29a910541441)

            - Above graph gives details on each point and its significance
            
![56](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/4d248083-69ea-4c8f-9960-0539097248b9)



         - 
   ### L6) Lab steps to gitclone vsdstd cell design
            - We need to perform a git clone here from a repository that we require, to do the future labs.
            - We can type the following command
                  ```
                  git clone https://github.com/nickson-jose/vsdstdcelldesign.git
                  ```

            - Now we need to copy the 'sky130A.tech' file into the directory we just cloned
            - We can do this by using
                  ```
                  cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
                  ```
                  ```
                  magic -T sky130A.tech sky130_inv.mag & 
                  ```  
             in the follwoing directory shown in the figure

![57](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/52248a0a-e99f-4749-8c53-84f4aa90970f)




  
## 2) INCEPTION OF LAYOUT CMOS FABRICATION PROCESS

### L1) Create Active Regions
           - Selecting a subsrate ( p-type, High resistivity, Doping level,oreintation )
           - Creating active region for transistors
                     - Step1 -> Deposit the kayer of photo resist
                     - Step2 -> Mask1 the region (protecting)
                     - Step3 -> So the UV rays doesnt hit the photoresist layer which is under Mask.
                     - Step4 -> Silicon layer is etched off in the Non masking region.
                     - Step5 -> Remove the Photoresist
                     - Step6 -> Placed in an oxidation furnance
                     - Step7 -> Isolation area will be created This process is called as LOCUS.

![58](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/7c3abbba-f06d-4fbd-a6f7-8bdcc9ca70f6)



![59](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/6f164cf2-6c53-4cbc-a7a3-51c2fdc8fa58)


### L2) Formation of N-well and P-well
                   - Step1 -> Photoresist the Layer
                   - Step2 -> Mask2 in the required region
                   - Step3 -> Expose the photoresist to UV rays
                   - Step4 -> Non masking area will be wanished
                   - Step5 -> Create a P-well ,It is created by using BORON
                   - Step6 -> Create a N-well ,It is created by using Phosphorous
                   - Step7 -> Take the complete structure into High Temperature Furnace
                   - Step8 -> This diffuses the wells and make proper n-well and p-well, This is called as twin tub process

![60](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/c1b40fea-c4ca-4908-95e0-1d9f364ed34c)



![61](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/558e401a-7916-422e-af6e-c08967559833)



### L3) Formation of gate terminal
                   - Step1 -> Gate formation involves depositing a gate oxide
                   - Step2 -> Defining gate patterns using photolithography
                   - Step3 -> Depositing gate material
                   - Step4 -> Etching to create gates
                   - Step5 -> Doping the substrate and insulating the gates.

![62](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/64326d5f-bd3d-4e1e-961b-824909c9aa73)


![63](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/06a33430-fc6e-4eef-886b-965c840dab53)


### L4) Ligtly dopped drain (LDD) formation
                   - Lightly doped drain (LDD) formation involves implanting the drain and source regions of a MOSFET transistor with a lighter concentration of dopants to reduce hot 
                     electron effect and short channel effect and enhance device performance.
                   - Doing both  n+ impantation and p+ implantation.
                   - It involves plasma etching here
                   
![64](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/f89ae9a6-80ec-4293-9a2b-6766aedb963b)



![65](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3577c510-5385-409b-ad50-121145b19513)


                            
### L5) Source and drain formation
                  - Source and drain formation in a MOSFET transistor typically involves doping the silicon substrate with chemicals such as arsenic or phosphorous for n-type regions 
                  (source and drain) and boron for p-type regions (source and drain).
                  - Here the source and drain are done by using ARSENIC method
                  - High temperature annealing is performed.

![66](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/40f02ef1-f824-4421-8456-dd6e58a05482)


![67](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/4904426d-6672-4765-a21f-d94ab0a13564)



### L6) Local interconnect formation
                  - Steps to form Contacts and Interconnects(local) 
                      - Step1 -> Titanium is deposited with a process known as sputtering. 
                      - Step2 -> Wafer is heated to about 650 - 700 C in an N2 ambient furnace for 60 seconds. 
                      - Step3 -> TiSi2 contacts are formed.  TiN is also formed used for local communication. 
                      - Step4 -> TiN is etched using RCA cleaning.

![68](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/0206e869-b7f1-4e9a-802e-3d1357a8f754)



![69](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/e0b0688c-da4f-44b7-93d2-2566a2b5a63d)

                      
### L7) Higher level metal formation
                 - Step1 -> Forming contacts and interconnects locally involves depositing a dielectric material like silicon dioxide
                 - Step2 -> Patterning it using photolithography
                 - Step3 -> Eetching contact holes 
                 - Step4 -> Depositing a barrier metal (e.g., titanium or titanium nitride)
                 - Step5 -> Filling with a conductor (e.g., aluminum or copper) using chemical vapor deposition (CVD)
                 - Step6 -> And then planarizing through chemical-mechanical polishing (CMP).

![70](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/c213585f-d7f8-48af-ae60-eb18ca45754d)



![71](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/969f5392-509d-4a1e-9372-0278fd34ae04)


![72](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/85ef95d2-1913-43eb-bfbc-d8aabc0d03d7)



### L8) Lab introduction to Sky130 basic layers layout and LEF using inverter

                - Now let us look at the layout of a CMOS inverter. To open this we type the command

![73](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/7da13277-bc74-4bdd-8c36-5728226803d2)


                - Now run the command 
                     > magic -T sky130A.tech sky130_inv.mag &
                - The following layout will be displayed.

![74](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/f9aca95c-ecb0-4e8c-a874-1c805a370a09)



                - We can get to know the details of the inverter by hovering the mouse cursor over it and pressing 's' on the keyboard. 
                - Then we can type what in the tkcon. 
                - Pressing 's' three times will show what parts are connected to the selected part.
                - We shall look at the difference between LEF and Layout. The above image is a Layout.
                - LEF represents abstract component data in a machine-readable format for IC libraries, while layout is the physical geometric arrangement 
                  of these components on a semiconductor chip.


                 
### L9) Lab steps to create std cell layout and extract spice netlist

![75](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/caa74ddb-bd3f-440e-8612-1849835f5bc3)



                - DRC error can be veiwed on the tkcon
                - To extract Spice Netlist we perform the following steps in the tkcon window:

![76](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/f124ab89-887d-4169-9c28-b64b6ae2c105)





                - We use the commands
                       > ext2spice cthresh 0 rthresh 0 -> this is done to copy the parasitic capacitances
                - The next command is
                       > ext2spice
                - We can see that a sky130_inv.spice file will be created


![77](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/39c22427-1595-46c6-9545-b255889ecd84)

## 3) SKY130 TECH FILE LABS

### L1) Lab steps to create final SPICE deck using Sky130 tech
               - To start off we look at the minimum value of the layout window

![78](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/9320e4eb-c8ac-4331-990c-388995fb004d)



               -  We can use 'g' on the keyboard to activate the grid and after selecting a grid by right clicking on the mouse, we type box in tkcon window to check the 
                  minimum value of the layout window


![79](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/cd058989-6588-4e30-aa47-54c3240794e1)


### L2) Lab steps to characterize inverter using sky130 model files
               - Next we need to open the spice file using the command
                        > gedit sky130_inv.spice
               - We need to configure it to the above specifications.
               - Characterize Inverter using Sky130 Models

![80](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3fa50420-0420-4905-8d0a-742d989402de)

               - We now plot the graph for output vs input sweeping the time.
               - We first use the command
                        > ngspice sky130_inv.spice
               - In the ngspice shell we use the command
                        > plot y vs time a
               - The following graph will be displayed

![81](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/3dc48d44-85af-4574-b181-b1f7b378cf4e)



![82](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/8f82f8ac-c9e1-4d2e-a28d-6d33eb6d6c6b)



![83](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/6a372b9b-f74a-4353-be7d-5ec6d7a5befa)


#### Rise Time -> time taken to rise from 20% to 80% of the max value -> 2.25075e-09 - 2.184e-09 = 0.006675e-09 s.


![84](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/92298000-aa22-4eec-acaa-7977edcd3ebc)



![85](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/8a36ff52-6eee-4849-8e2e-81a63f887e8f)


#### Propogation Delay/Cell Rise Delay -> 2.21379e-09 - 2.15e-09 = 0.06379e-09 s.


### L3) Lab introduction to Sky130 pdk's and steps to download labs
               - Enter the command
                       > wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
               - Move the fikes into the desktop using the below command
                       > mv drc_tests.tgz Desktop/
               - Extract the file using the folloeing command
                       > tar xfz drc_tests.tgz 
               - Check the files inside it using ls command

![86](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/63c281c7-9b8d-4d3a-8aa9-c81a047286d9)




![87](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/0b551da5-973d-4b91-87d4-2174b065bc4b)

    
     
    
### L5) Lab introduction to Magic and steps to load Sky130 tech-rules

            - To open the software we type
                 > magic -d XR

![88](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/dd1f6fd5-e4a2-4f03-a963-2d64ff16a995)


![89](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/42855e38-be5c-41c2-a45a-fea26582b959)


            - Selct M3 by clicking left an right button in the mouse , select an area M3
            - And then tpe this command in the tkcon window It shows a DRC error 
                 > drc why
                   
![90](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/e6d8eb36-7660-43a9-afc6-8b4ac0c4764d)


            - To add contact cuts to metal3, first select an area using left and right click. Then hovering 
                over the m3contact we click middle mouse button.
            - To check the black boxes inside this, Type the following command 
                 > cif see VIA2

![91](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/c4ef0d76-3d2a-4bfe-81af-38d530a54724)



### L6) Lab exercise to fix poly.9 error in Sky130 tech-file
       - In magic file type the following command
            > load poly
       - There will a diff between the spacing of poly.9 
       - In order to over come this we need to sort the DRC error

![92](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/331f2d98-0a4e-400d-8d29-41c2f8ff5863)


       - There is a DRC error in the poly.mag file in 'poly.9'.
       - Open the sky130A.tech file in the editor and make the following changes
             > vi sky130A.tech 
       - Add this line in the editor 
             >  spacing xhrpoly,uhrpoly,xpc allpolynonres 480 touching_illegal \
                     "xhrpoly/uhrpoly resistor spacing to diffusion < %d (poly.9)"

             > spacing npres allpolynonres 480 touching_illegal \
                     "poly.resistor spacing to N-tap < %d (poly.9)"
              
![93](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/8a237891-b5e6-490c-a0b5-16e2e7053cae)


![94](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/c2e2b280-4145-49c4-93b3-844316aa82a8)


      - Now open the tkcon window and type 
            > tech load sky130A.tech
            > drc check 
      - Now we can see that the DRC eroor will be solved 
      
![95](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/4075e2cb-8c64-4334-90fb-f4cd79858fcd)

  

### L8) Lab challenge exercise to describe DRC error as geometrical construct
      - Now we open the nmwell.mag file
      - Open the tkcon window and type the following command
           > cif ostyle drc
           > cif see dnwell_shrink
           > cif see nwell_missing
     - The following window appears

![96](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/54c4e8fd-ada5-485c-a8e4-f6d80ecfb530)



### L9) Lab challenge to find missing or incorrect rules and fix them
       - Add nsubstratencontact somwhere into the nwell

![97](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/ec71af56-04e6-4351-9fe0-661dfc67b7e3)

      
       - And then make these changes in the editor file
          > cifmaxwidth nwell_untapped 0 bend_illegal \
              "Nwell missing tap (nwell.4)"

![98](https://github.com/madhumadhu1318/Pes_Openlane_work/assets/90201844/b22df32c-0a89-4b8f-b738-7695d77b3e69)


       - type the following commands in the editor file
          > templayer nwell_tapped
            bloat all nsc nwell
          > templayer nwell_untapped nwell
            and-not nwell_tapped
          


          > variants (full)
            cifmaxwidth nwell_untapped 0 bend_illegal \
              "Nwell missing tap (nwell.4)"
            variants *


      - Type the following commands in the tkcon window
            > tech load sky130A.tech
            > drc check
            > drc style drc(full)
            > drc check
      - The following window will appear

  
      - Now if we select 'nsubstratencontact' somwhere inside the cell The problrm is solved
       
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d0590dd2-8681-4c1b-a4cd-3a2c95b719c9)




[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 4 : Prelayout timming layout analysis and inportance of good clock tree </summary>
<br>

## 1) TIMMING MODELLING USING DELAY TABLES

### Lab challenge to find missing or incorrect rules and fix them

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7caa9c46-1f7b-4c44-a849-d023b7d3dba9)

       - Converting grid info into Track info
       - Go to openlane directory / sky130_fd_sc_hd 
       - type less tracks.info

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b5bde9d6-5d95-4452-aec7-138935f5cefb)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/be3f5c92-6ef6-4ab2-8493-078e2ca01cc6)

      - Here 1st value indicates the offset and 2nd value indicates the pitch along provided direction

 
 ### Setting grid values using above file info

        - ext2spice 
        - help grid
        - grid 0.46um 0.34um 0.23um 0.17um

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5a6ae931-fa7f-4dc5-9624-489a53ffe754)


### Before grid vs After grid

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/7caa9c46-1f7b-4c44-a849-d023b7d3dba9)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/bec49fed-8a12-4cf5-ae15-cb9fb811da01)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/592a608a-8bed-4c5c-b0e2-7abe6cb3a418)

        - From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
        - The PR boundary is taking 3 grids on width and 9 grids on height which says that the 2nd condition is also met



## GENERATION OF A LEF FILE
        - Once the layout is perfect we can generate the lef file
        - In the tkcon window type the following command to save the updated layout
              > save sky130_vsdinv.mag
        - once it is saved then go to the terminal window and the type 
              > magic -T sky130A.Tech sky130_vsdinv.mag &
        - A magic layout opens , In the tkcon window type 
              > lef write

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f249106d-9204-4870-9122-1c2b5707cbf2)

        - Once this is done lef file should be created in the vsd file

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a969dff8-b8e6-45fd-9827-7938aaa223fb)

        - To open the lif file type the below command in the terminal
              > less sky130_vsdinv.lef

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8b5a5093-f378-4373-b4cf-43decea2ff80)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/63a7e1f5-e878-48a3-91d3-0430f89a5a85)


## STEPS TO INCLUDE NEW STEPS IN THE SYNTHESIS

        - Open the picorv32a pwd in the terminal
        - copy the path 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/59c7483e-40b2-4d23-b7c7-123fac3364c7)

        - Go to the vsdstdcelldesign in the other terminal type 
              > cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/722778fc-c141-4d4d-b8f2-793d16a3f0eb)

        - Now if u check in the picorv terminal, the lef file will be copied 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/37de186e-57d2-4d89-a027-99fc34d1544e)

        - Modify the config.tcl by
             > vim config.tcl
        - In the design's config.tcl file add the below line to point to the lef location which is required during spice extraction.
               > set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
        - Include the below command to include the additional lef into the flow:
               > set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
               > add_lefs -src $lefs
        - Run the interactive mode 

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8ffe7b20-d457-4a99-84a9-0f5188025722)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/6cf04c38-6989-4132-87e7-4ca2e190ef5c)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/68f1a325-8ae7-4b94-865f-8938136c0c1d)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4fefa4c4-77b6-4e45-b0d7-86d7bd3e830b)

- since there is slack, we have to reduce it
      VLSI engineers will obtain system specifications in the architecture design phase. These specifications will determine a required frequency of operation. To analyze a circuit's 
      timing performance designers will use static timing analysis tools (STA). When referring to pre clock tree synthesis STA analysis we are mainly concerned with setup timing in regards to a 
      launch clock. STA will report problems such as worst negative slack (WNS) and total negative slack (TNS). These refer to the worst path delay and total path delay in regards to our setup 
      timing restraint. Fixing slack violations can be debugged through performing STA analysis with OpenSTA, which is integrated in the OpenLANE tool. To describe these constraints to tools such 
      as In order to ensure correct operation of these tools two steps must be taken:

           Design configuration files (.conf) - Tool configuration files for the specified design
           Design Synopsys design constraint (.sdc) files - Industry standard constraints file

     For the design to be complete, the worst negative slack needs to be above or equal to 0. If the slack is outside of this range we can do one of multiple things:

   ### 1) Review our synthesis strategy in OpenLANE

                     - Enalbed CELL_SIZING
                     - Enabled SYNTH_STRATEGY with parameter as "DELAY 1"
                     - The synthesis result is :

           - To run the floorplans and placements we typr the following commands
                > run_floorplan
                > run_placement
  
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b805d7ea-354d-4e41-b761-e86cdf57dc20)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8e3b333a-35f9-4830-9e18-fa25f2be744f)


             - magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/cf2dec3c-046d-41ee-9e25-a89e53c5b1d7)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d50f0c5e-3b2a-4069-aaad-f24e8a395687)




## TIMMING ANALYSIS WITH REAL CLOCKS USING OPEN STA

         - Configure OpenSTA for Post-Synth Timing Analysis
         - We must create two files
              - The first one must be in the openlane directory
              - This file is known as the 'pre_sta.conf' file.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/aeec25c6-c897-4218-be0b-62a048c76a54)

              - The second is the my_base.sdc file.
              - This should be in the 'src/sky130' directory under the picorv32a directory.
             
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/d73a4a04-6bbf-4010-b7f2-8c3427dd0b12)

              - To run tyming analysis we type 
                    > sta pre_sta.conf

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/ac22c1af-3022-4ad5-b5b8-e4427e1bc888)

             - There is a slack violation
             - Settinf MAX_FANOUT value to 4 reduces the slack violation.

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/1a62d227-1a3c-4a71-880d-cf7dd8b45eb6)


## Clock Tree Synthesis TritonCTS and Signal Integrity
### Run CTS

             -  To run CTS we need to type the command
                       > run_cts
                       > New .v is created

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b1f93411-14b4-4f47-b523-4c1d7eb71913)

#### Timing Analysis with Real CLocks using OpenSTA

             - First we type the command 
                    > openroad.
             - Then we read the .lef file using the command
                    > read_lef /openLANE_flow/designs/picorv32a/runs/16-09_19-58/tmp/merged.lef

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/f59877a7-4736-4229-94c6-305a1b1c0ad6)

              - Then we read the .def file.
                     > read_def /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/cts/picorv32a.cts.def

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/4252f6d9-60ca-482c-b9a5-08c817848f84)

              - Then we type the below commands
                     > write_db pico_cts.db
                     > read_db pico_cts.db
                     > read_verilog /openLANE_flow/designs/picorv32a/runs/16-09_19-58/results/synthesis/picorv32a.synthesis_cts.v
                     > read_liberty -max $::env(LIB_SLOWEST)
                     > read_liberty -max $::env(LIB_FASTEST)

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/9f159716-cc50-4088-904f-9fadb4184353)

              - We read the .src file
                    > read_sdc /openLANE_flow/designs/picorv32a/src/sky130/my_base.sdc

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/22e69c85-7822-44ee-a544-fb9cad238a1d)

              - We set the clock and then check it
                    > set_propagated_clock [all_clocks]
                    > report_checks -path_delay min_max -format full_clock_expanded -digits 4

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/b23d8d20-7df9-485c-af23-44a2f6fde7ff)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/a0ac65cd-eb98-4df7-8b0d-bd4127d033f8)


              - We perform it again for the more accurate result
              
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/215dd64d-4a1a-4e68-bf06-a89273648a12)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/8e7259aa-ab61-4bb9-b2c0-fbbf47fbe6d2)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5d16114e-0883-42d1-886b-b064d5426d76)

              -  Next type the following commands 
                   > report_clock_skew -hold
                   > report clock_skew -setup

![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/86212a96-c004-49c9-824b-3b69c66927f3)



[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)

</details>
<details>
<summary>DAY 5 : Final steps for RTL2GDS using triton route and openSTA </summary>
<br>

## Power Distribution Network and Routing

After generating our clock tree network and verifying post routing STA checks we are ready to generate the power distribution network gen_pdn in OpenLANE:

     The PDN feature within OpenLANE will create:

          Power ring global to the entire core
          Power halo local to any preplaced cells
          Power straps to bring power into the center of the chip
          Power rails for the standard cells

   ### Build Power Distribution network
   
![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/5d1ea9af-11c2-4200-8fb4-ac7850ffa1dd)


![image](https://github.com/Vinodkumar8318/Pes_Openlane_work/assets/142583979/1f2915be-f8fc-4fb4-a192-3e2c30afa917)


   ### Global and Detailed Routing

   - OpenLANE uses TritonRoute as the routing engine run_routing for physical implementations of designs. Routing consists of two stages:
           > Global Routing - Routing guides are generated for interconnects on our netlist defining what layers, and where on the chip each of the nets will be reputed
           > Detailed Routing - Metal traces are iteratively laid across the routing guides to physically implement the routing guides

   - If DRC errors persist after routing the user has two options:
           > Re-run routing with higher QoR settings
           > Manually fix DRC errors specific in tritonRoute.drc file

  ### SPEF Extraction

    - After routing has been completed interconnect parasitics can be extracted to perform sign-off post-route STA analysis. The parasitics are extracted into a SPEF file. The SPEF extractor 
      is not included within OpenLANE as of now.
           > cd ~/Desktop/work/tools/SPEFEXTRACTOR
           > python3 main.py <path to merged.lef in tmp> <path to def in routing>
    - The SPEF File will be generated in the location where def file is present


[Back to COURSE](https://github.com/Vinodkumar8318/Pes_Openlane_work/tree/main#course)
