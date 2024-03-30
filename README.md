
# Digital-Soc-Design

# Day 1
The LAB for day 1 gives the complete flow about using the SKYWATER 130nm PDK, Openlane EDA

## Open the working Directory


![Going to location](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/a83627bd-2320-42f9-b172-37c3b89ddce4)

```bash
  cd Desktop
  cd work/tools
  cd openlane_working_dir
  cd openlane
```

## To open the Openlane
![openlane initiation](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/0dec4218-a1ef-4757-bcf7-4ee7700359aa)

After getting into the directory, enter the commands
```bash
  docker
  pwd
  ls -ltr
```
To open the openlane in interactive mode, 
```bash
 ./flow.tcl -interactive
```
To prepare the openlane,

```bash
  package require openlane 0.9
  prep - design picorv32a
```
## Synthesis
To run the Synthesis
```bash
 run_synthesis
```
![synthesis](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/75ebcd4f-1af6-480c-ab77-be2ff9a9428e)

-> After Synthesis is completed, the message is shown that the "Synthesis was successful"

-> This contains all the details about the synthesis of the picorv32a 

- The Chip Area of the module 147712.918400
  ![chip area](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/982757d8-6d38-4bf5-be5b-f1b1f15f091f)

- Number of cells: 14876
  ![no of cells](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/51b13fb1-c4aa-4017-b5c0-b38dd68ee8fb)

- Number of FF: 1613
  ![no of flip flops](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/94f74ba1-b666-4017-838f-1e86e1e3d797)


-> Particularly we are interested in finding the Flop ratio.
This can be calculated by using the formula:
                 
             Flop ratio in (%) = Total No of D-FF
                               --------------------  X 100
                                Total No of Cells

                              = 1613
                              --------   X 100
                                14876 

                              = 10.8429685


## Synthesis Report
The Synthesis Report are found in the directory

```bash
   ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/reports/synthesis/1-yosys_4.stat.rpt
```

The synthesis Results are found in the directory

```bash
   ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/results/synthesis/picorv32a.synthesis.v
```

# Day 2

## Floorplanning
The LAB for day 2 gives the complete flow of the Floorplanning and the placement process

After the Synthesis process, type the command for running the Floor planning
![configuration directory](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/9deff139-100d-46e8-bd5a-299aed36ec33)

The configuration files are inside the location
```bash
  /Desktop/work/tools/openlane_working_dir/openlane/configurations/README.md
```
To run floorplan
```bash
  run_floorplan
```
we will be getting a success message like this
![floorplan_success](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/3e474461-9d16-4e7b-a702-0b0836335026)

In this particular location from the floorplan.def file, we can able to see the area of the chip
![area](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/2311ce1a-dc24-4094-b6a9-c2adf3df642d)


             1000 unit distance = 1 Micron

             Distance in micron = value
                                ----------
                                   1000

            Die width in micron = 660685 
                                 ---------
                                   1000
                                
           Die height in micron =  671405 
                                  ---------
                                    1000

          Area of die in micron = 660.685*671.405 Square micron 

Open this directory to initiate the Magic Tool
![magic location](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/5079d8cd-f95b-4776-a4aa-83dc5f4722f3)

Locate to this directory
```bash
  ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/results/floorplan
```

```bash
 magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
- Floorplan def in Magic
![magic opening](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/c8336e8f-68d8-45f6-a46a-428b21e6a19b)



- Horizontal metal layer
![horizontal metal layer](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/8bc0e87d-fb4d-41c9-9d48-373f1ba65d4e)


- Vertical metal layer
![vertical metal layer](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/dc0da0f0-9cd7-49a5-a5a7-9dbcf22a91df)

- Standard cells
![standard cells](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/f388ecb6-ed25-4814-bc2e-37fe628ad201)

## Placement
To run the Placement, the command is
![run placement](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/1c2cf0a3-7b9d-4f59-9ad0-2eea22a6f466)

```bash
    run_placement
```
Commands to load placement def in magic
![placement location](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/433d133e-f0a8-45f9-8a95-eaaf79077762)

```bash
    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
- Floorplan def in magic

![placement chip](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/2b8c7816-ecd2-4977-b9ab-3d4d27b021b2)

- Standard cell placement

![placement of standard cells](https://github.com/SANGESH007/Digital-Soc-Design/assets/77070030/34c89e7c-60b0-4c62-a0c2-239ab8587e28)



