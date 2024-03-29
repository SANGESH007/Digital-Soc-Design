
# Digital-Soc-Design

## Day 1
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
