# Lecture 12 - NEB-TS Calculations 

October 2, 2025

In today's hands-on, we are going to prepare an input file for a NEB-TS calculation using ORCA. 

You should look at the CH<sub>2</sub>OH to CH<sub>3</sub>O proton transfer reaction. 

Note that this is the reverse reaction compared to what is considered in the lecture slides and the example files. 
Thus, in this case, CH<sub>2</sub>OH is the reactant and CH<sub>3</sub>O is the product. 

Note that the molecule is neutral and a doublet, so you must take that into account in the calculations. 

You should perform the simulations using B3LYP+D3 and the Def2-SVP basis set. 

### Preparing the ORCA Input File and Running it

You can copy files needed from the following folder:
```
/storage/nas_scr/shared/groups/compchem-chem5600/Lectures-2025/Lecture-15_October-2-2025/NEB-TS_CH2OH-CH3O_InputFiles
```

This includes the input file and XYZ files for the reactant and product. 

You will need to edit the input file  `NEB-TS_CH2OH-CH3O.inp` to add the relevant reactant and product XYZ files, and the appropriate keywords for the level of theory. You also need to add the keyword for the NEB-TS calculations. 

Note, in this case, CH<sub>2</sub>OH is the reactant and CH<sub>3</sub>O is the product. Make sure that this is correctly specified in the input file. 

Once you have the input file, you should submit it using the ORCA wrapper. 

**Note, you should use ORCA 5.0.3 for the calculations**.  

I recommend using 18 cores for the calculations and specifying 64 GB of memory. 

The calculation should take around 3-4 minutes. 

### Analyzing the Results 

Once the calculation has finished, take a look at the initial guess for the NEB using molden:
```
molden <input file>_initial_path_trj.xyz
```
Does this path make sense? 

You should also take a look at the converged NEB minimum energy path:
```
molden <input file>_MEP_trj.xyz
```
How does this path compare to the initial NEB guess?

You should also look at the converged transition state structure:
```
molden <input file>_NEB-TS_converged.xyz
```
Does this transition state structure make sense? 

Check the vibrational frequencies for the transition state structure. Does it have a single imaginary frequency as it should? 

You can also look at the energies along the NEB minimum energy path by plotting the `<input-file>.final.interp` file, for example using gnuplot:
```
plot '<input-file>.final.interp' u 1:3
```













