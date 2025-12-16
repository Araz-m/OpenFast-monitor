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
##  Usage
### 1. Configure Input File and Time Settings

In the script, define:

- The path to the OpenFAST .out file

- Simulation time range

- Simulation time step (must match the OpenFAST configuration)

```bash
file_path = "path/to/your/OpenFAST.out"
simulation_time_range = (start_time, end_time)
simulation_time_step = dt
```
### 2. Configure Plot Groups

Users define which output channels to visualize by creating plot groups. Each
group consists of:

- A list of OpenFAST output column names

- A corresponding list of scaling factors

Example:

```bash
plot_groups_1 = {
    "Optimus 20MW-295": (["Wind1VelX", "BldPitch1", "RotSpeed", "RotTorq", "RotPwr", "GenPwr"], 
                [1, 1, 1, 0.001, 0.001, 0.001]),
    "Tip Clearance": (["Tip2Twr1", "Tip2Twr2", "Tip2Twr3"], 
                [0.001, 0.001, 0.001, 0.001])
}
```

Column names must exactly match those in the OpenFAST .out file. Scaling factors
allow normalization or unit adjustment for clearer visualization.

Additional plot groups can be enabled in the script as needed.

### 3. Run the Script

To enable real-time monitoring while the simulation is running:
 
```bash
real_time=True
```
For post-processing of completed simulations:

```bash
real_time = False
```
The script can be executed from any Python environment (e.g. VS Code terminal).

## 📸 Example Outputs

### Single Plot Group Example 

https://github.com/Araz-m/OpenFAST-Output-Monitor/blob/main/Figure_1_Example.png

### Multiple Plot Group Example

https://github.com/Araz-m/OpenFAST-Output-Monitor/blob/main/3%20sets%20of%20figures_Example.png


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

