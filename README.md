### IHSD
This script is for calculating Permeability Coefficient (P) of a small molecule through a lipid bilayer from PMF and Diffusion Coefficients (DC) using Inhomogeneous Solubility Diffusion Model.

<br> 'IHSD' calculates Permeability Coefficient 'P' by integrating Resistivities 'R' over the reaction coordinate 'z'. 
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
  `[P, R] = IHSD('PMF.csv', 'DC.csv', [-3.8:0.01:3.8], 0.008314463, 303.15)`
