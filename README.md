# OpenFast-monitor

# Real-time & Post-Processing Visualization Tool

A Python tool for live monitoring and analysis of OpenFAST wind turbine simulations. Automatically plots parameters from `.out` files during execution (real-time) or after completion, eliminating manual Excel charting and handling thousands of data points seamlessly.

**Visualize key metrics like:** Wind speed, blade pitch angles, rotor speed, tower loads, power output, and structural responses - all in customizable, auto-updating plots.

## 📌 Features
- ✅ **Real-time data plotting** with Matplotlib animations.  
- ✅ **Automatic file monitoring** – waits for the simulation output file to be available.  
- ✅ **Multiple plot groups** – easily configurable for different sets of parameters.  
- ✅ **Dynamic axis scaling** for improved readability.  
- ✅ **Interactive plots** that automatically update as new data is written to the file.
---

## 🚀 Installation & Setup
### 1️⃣ Install Dependencies
Make sure you have **Python 3.10+** installed. Then, install the required libraries:

```bash
pip install pandas matplotlib numpy
```

---
## ⚙️ Usage
### Configuring Plots
You can define different plot groups in the script by modifying:

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
Run the OpenFast_Output_Viewer Script (I used VSCode Terminal)

## 📸 Sample Output
### 1 Set Example: 
https://github.com/Araz-m/OpenFast_Output_Viewer/blob/main/Figure_1_Example.png
### Multiple Set Handling:
https://github.com/Araz-m/OpenFast_Output_Viewer/blob/main/3%20sets%20of%20figures_Example.png

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

