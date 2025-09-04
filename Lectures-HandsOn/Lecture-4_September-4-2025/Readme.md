# Lecture 4 - Assignment 1

Sept 4, 2025 

You should work on Assignment 1, which has just been posted on Canvas.

You should start by creating a new sub-folder under `Runs` for this assignment. 

## Geometrical Optimization 

The first step is to perform geometrical optimization starting from the initial geometry you got from the SMILES/InChl strings.

Start by getting initial coordinates by using a SMILES string from PubChem. You can use the [Jupyter notebook](https://colab.research.google.com/github/valsson-group/UNT-Chem-4660-5660-Fall2025/blob/main/Python-JupyterNotebooks/SMILES_Molecular_Representations.ipynb) shown in class to do this. Make sure that this initial geometry looks reasonable.

You should perform a geometrical optimization using the DFT/B3LYP+D3 and the cc-pVDZ basis set. 

In Gaussian 16, the keyword for geometrical optimization is `OPT`. You should look into the Gaussian manual for [DFT](https://gaussian.com/dft/) to find the correct keywords to activate the D3 dispersion correction. 

Once you have created the input file, you can submit the calculation using
```
g16 -i <FILENAME>.gjf -p compchem.36 -c 9 -m 16gb -s local
```

Once the calculation has finished, verify that it was completed correctly. 

You can look at the geometries obtained during the optimization using `molden`
```
molden <FILENAME>.log
```

You can extract the final geometry using the `get_g16_co` script:
```
get_g16_co <FILENAME>.log
```

This will create a file named `outcoo.xyz` that has the XYZ coordinates (in units of Angstrom) for the final geometry. Here, we will rename this file so that it has the same prefix name as the input file 
```
mv outcoo.xyz <FILENAME>.final.xyz
```
You can then look at this geometry using molden:
```
molden <FILENAME>.final.xyz
```

You can also perform the geometrical optimization using ORCA by using the `OPT` keyword; see below for further information about the structure of the ORCA input file. One benefit of using ORCA is that it will, at the end of the simulation, create a new file with the coordinates of the optimized geometry with the filename `<FILENAME>.xyz`.


## Gaussian 16 - Single Point Calculations 

Using the DFT/B3LYP+D3 geometry obtained from the geometrical optimization, you should perform single-point calculations using HF, DFT/B3LYP, DFT/B3LYP+D3, and DFT/PBE0+D3. You should use the same basis set as for the geometrical optimization, cc-pVDZ. 

You should now create new Gaussian input files for performing the single-point calculations on this geometry. 

For example, for the HF, you should use the following keywords for the calculation:
```
# HF/cc-pVDZ
```
to indicate that you are doing a Hartree-Fock (HF) calculation using the cc-pVDZ basis set. Note that there should be no `OPT` keyword, as we are performing a single-point calculation on this geometry. 

Make sure that you also change the `%chk=` keyword so it fits with the filename of the input file, for example:
```
%chk=<FILENAME>.chk
```
if you use the filename I suggested. 


You will now need to submit the calculations using the `g16` wrapper discussed in previous lectures. I would suggest using only 4 cores for the calculation (`-c 4`)


## ORCA 6 - Single Point Calculations 

You should now do the same calculation with ORCA 6 code, another quantum chemistry code we will use throughout the course. 

For ORCA 6, the [manual](https://www.faccts.de/docs/orca/6.0/manual/index.html) and [tutorial](https://www.faccts.de/docs/orca/6.0/tutorials/index.html) are helpful to understand how the input file should be structured
- [4. General Structure of the Input File](https://www.faccts.de/docs/orca/6.0/manual/contents/structure.html)
- [5. Input of Coordinates](https://www.faccts.de/docs/orca/6.0/manual/contents/input.html)

For example, a HF single-point calculation is discussed in [this tutorial](https://www.faccts.de/docs/orca/6.0/tutorials/prop/single_point.html). The first example in this tutorial shows how to do an HF calculation. 

Information about appropriate keywords for the DFT functionals and dispersion correction can be found in [Section 7.4 of the manual](https://www.faccts.de/docs/orca/6.0/manual/contents/detailed/model.html#)

Create ORCA input files for doing single-point calculations on the same geometry as you did using Gaussian. 

The format of the input file should be something like this:
```
!HF cc-pvdz
* xyz 0 1
<INSERT XYZ COORDINATES HERE>
*
```

You can then submit the orca input file using the `orca` wrapper that works in similar way as the `g16` wrapper. The main difference is that you will need to specify the version; here we will use version 6.1.0 of ORCA that is the latest version.
```
orca -i <FILENAME>.inp -p compchem.36 -c 4 -m 16gb -s local -v 6.1.0
```
You should check the output file to ensure that you are using the correct version 6.1.0. 







