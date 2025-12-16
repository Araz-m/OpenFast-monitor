# OpenFAST-Output-Monitor

A Python-based tool for real-time and post-processing visualization of OpenFAST
wind turbine simulation outputs.

This script supports academic and engineering workflows by enabling quick visual
inspection of OpenFAST `.out` files during simulation execution or after
completion.

---

## Overview

OpenFAST simulations, especially Design Load Case (DLC) studies, often run for
many hours and generate large output files. This tool allows users to monitor
key simulation variables in real time or analyze results after completion,
without manual post-processing in spreadsheet software.

The script reads OpenFAST output files, groups user-defined signals, and produces
interactive plots that automatically update as new data becomes available.

---

## Key Capabilities

- Real-time monitoring of OpenFAST `.out` files during simulation runs
- Post-processing visualization of completed simulations
- Automatic detection of output file creation and updates
- Configurable plot groups for different physical quantities
- Dynamic y-axis scaling for improved readability
- Interactive Matplotlib figures suitable for long-running simulations

---

## Typical Use Cases

- Monitoring long-running DLC simulations without manual intervention
- Quickly validating simulation behavior during execution
- Visual inspection of operational parameters, loads, and structural responses
- Reducing reliance on manual Excel-based plotting for large datasets

---

## Installation

### Requirements

- Python 3.10 or newer

### Dependencies

Install the required Python packages:

```bash
pip install pandas matplotlib numpy
```
---
## ⚙️ Usage
### 1. Configure Input File and Time Settings

In the script, define:

- The path to the OpenFAST .out file

- Simulation time range

- Simulation time step (must match the OpenFAST configuration)

```bash
plot_groups_1 = {
    "Optimus 20MW-295": (["Wind1VelX", "BldPitch1", "RotSpeed", "RotTorq", "RotPwr", "GenPwr"], 
                [1, 1, 1, 0.001, 0.001, 0.001]),
    "Tip Clearance": (["Tip2Twr1", "Tip2Twr2", "Tip2Twr3"], 
                [0.001, 0.001, 0.001, 0.001])
}
#==============================================================================
#uncomment plot_groups_2 if you need to plot more groups 
# if you did, remember to add <plot_groups_2> in the plot_multiple_groups function at the end
#==============================================================================
# plot_groups_2 = {
#     "Loads on blade Root_I": (["RootFxb1", "RootFyb1", "RootFzb1", "RootMEdg1", "RootMFlp1", "RootMzb1"], 
#                 [0.001, 0.001, 0.001, 0.001, 0.001, 0.001]),
#     "Loads on blade Root_II": (["RootFxc1", "RootFyc1", "RootFzc1", "RootMzc1", "RootMzc2", "RootMzc3"], 
#                 [0.001, 0.001, 0.001, 0.001, 0.001, 0.001])
# }



#==============================================================================
#uncomment plot_groups_3 if you need to plot more groups
# if you did, remember to add  <plot_groups_3> in the plot_multiple_groups function at the end
#==============================================================================
# plot_groups_3 = {
#     "Loads on Tower Top_I": (["YawBrFxp", "YawBrFyp", "YawBrFzp"], 
#                 [0.001, 0.001, 0.001]),
#     "Loads on Tower Top_II": (["YawBrMxp", "YawBrMyp", "YawBrMzp"], 
#                 [0.001, 0.001, 0.001])
# }
#==============================================================================
```


you have to add the exact column name from your .out file and also you have to choose the scale that you need for the respected data in the list.

## When you have decided to run the real time simulation make sure that 
```bash
real_time=True
```
Run the OpenFAST-Output-Monitor Script (I used VSCode Terminal)

## 📸 Sample Output
### 1 Set Example: 
https://github.com/Araz-m/OpenFAST-Output-Monitor/blob/main/Figure_1_Example.png
### Multiple Set Handling:
https://github.com/Araz-m/OpenFAST-Output-Monitor/blob/main/3%20sets%20of%20figures_Example.png

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

