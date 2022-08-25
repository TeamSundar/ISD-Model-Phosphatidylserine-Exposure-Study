The codes used in the study **Radhakrishnan, N., Kaul, S. C., Wadhwa, R., & Sundar, D. (2022). Phosphatidylserine Exposed Lipid Bilayer Models for Understanding Cancer Cell Selectivity of Natural Compounds: A Molecular Dynamics Simulation Study. Membranes, 12(1), 64** (https://doi.org/10.3390/membranes12010064).
 
---
### dc_from_xacf.m

This function is for calculating position-dependent diffusion coeffcieints of small molecules through lipid bilayer after performing umbrella sampling MD simulations.
Diffusion Coefficient (DC) is calculated from Position Autocorrelation Function (XACF) using the Generalized Langevin Method of Hummer (https://doi.org/10.1088/1367-2630/7/1/034).

#### Two input arguments:
  1) **xacf_file**: Filename of calculated Autocorrelation functions for different umbrella sampling windows.
  <br>Example: 'xacf_window_%d.xvg'
  <br>In this case, the names of the files should be 'xacf_window_1.xvg', 'xacf_window_2.xvg', 'xacf_window_3.xvg', ...
  <br>The first column in file should contain Time (in ps), and the second coulmn should have the correlation coefficients.
  2) **i**: Total number of files   
  
#### Output:
  1) DC values of all umbrella sampling windows in a array.
  
<b>Example:</b>
  <br>`dc = dc_from_xacf('xacf_window_%d.xvg',20)`
  
---
### ISD.m
This script is for calculating Permeability Coefficient (P) of a small molecule through a lipid bilayer from PMF and Diffusion Coefficients (DC) using the Inhomogeneous Solubility Diffusion Model of Marrink and Berendsen (https://doi.org/10.1021/j100066a040).
'ISD' calculates Permeability Coefficient 'P' by integrating Resistivities 'R' over the reaction coordinate 'z'. 
#### 5 input arguments in the following order
1)  **pmf_file**:   CSV file with two columns, Reaction coordinate (in nm) in first column, PMF (Potential of Mean Force) values (in kJ/mol) in second column 
2)  **dc_file**:    CSV file with two columns, Reaction coordinate (in nm) in first column, DC (Diffusion Coefficient) values (in nm<sup>2</sup>/ps) in second column
3)  **z**:          reaction coordinate
4)  **kB**:         Boltzmann constant (in kilojoules per kelvin) 
5)  **T**:          Temperature (in K)
    
#### 3 output arguments in the following order
1)  **P**:          Permeability Coefficient (in nm/ps)
2)  **Re**:         Effective Resistivity (in ps/nm)
3)  **R**:          Resistivities (in ps/nm<sup>2</sup>)
    
#### Example
  `[P, R] = ISD('PMF.csv', 'DC.csv', [-3.8:0.01:3.8], 0.008314463, 303.15)`
 
