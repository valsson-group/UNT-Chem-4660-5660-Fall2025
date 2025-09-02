# Lecture 3 - Hartree-Fock calculations 

September 2, 2025 

Here, we will perform Hartree-Fock (HF) calculations using both Gaussian and ORCA 6 codes. We will consider a L-Tryptophan molecule.

You should start by creating a new sub-folder under `Runs` for today's runs. 

## Some Tips for using Cruntch4

- For Gaussian, it is best to use the extension `.gjf` for input files. 
- After submitting each calculation and it appears to have finished, you must always check the calculation finished correctly by opening the `<FILENAME>.log` file with `vi`.
- For Gaussian, the last line should read: “Normal termination of Gaussian 16 at ….” (Hint: you can go the last line by using `shift+g` in `vi`.
- The filenames I might write in the Hands On notes might be different to the ones that you use. Thus, you are likely to need to adjust the commands I give to the filenames you are using. 
- In other words, do not use the commands that I list blindly and do not follow the instructions blindly
- If a command that you are using gives some errors, spend a moment to investigate what could be the issue (e.g., the `get_g16_co` command)
  - Are there spelling errors in the command or filename
  - Are you using the correct filenames?
  - Does the file exist?
  - Did the  previous calculation finish correctly?
  - Etc..
- Double-check that the output of the command you are using gives what you are expecting (e.g., does the `get_g16_co` command give a xyz file with atoms, check that with vi).



## Gaussian 16 - DFT/B3LYP Geometrical Optimization 

We will consider a L-Tryptophan molecule. 

Start by getting initial coordinates by using a SMILES string from PubChem. You can use the [Jupyter notebook](https://colab.research.google.com/github/valsson-group/UNT-Chem-4660-5660-Fall2025/blob/main/Python-JupyterNotebooks/SMILES_Molecular_Representations.ipynb) shown in class to do this. Make sure that this initial geometry looks reasonable.

You should perform a geometrical optimization using the DFT/B3LYP and the cc-pVDZ basis set. The Gaussian keywords that you should use are `OPT  B3LYP/cc-pVDZ`. Note that this setup is the same as the one used in Lecture 1, so you can use the files from that lecture as a starting point to see how the input file should look like.

Once you have created the input file, you can submit the calculation using
```
g16 -i <FILENAME>.gjf -p compchem.36 -c 9 -m 16gb -s local
```

Once the calculation has finished, verify that it was completed correctly. 

You can look at the geometries obtained during the optimzation using `molden`
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


## Gaussian 16 - Hartree-Fock Calculations 

For the Hartree-Fock calculations, you should use the DFT/B3LYP geometry obtained from the geometrical optimization. You should use the same basis set as for the geometrical optimization, cc-pVDZ. 

You now should create a new Gaussian input file for performing HF calculations on this geometry. I suggest using the filename `L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz.gjf` to indicate the level of theory (HF/cc-pVDZ) and on what geometry the calculation is performed. 

You should use the following keywords for the calculation:
```
# HF/cc-pVDZ
```
to indicate that you are doing a Hartree-Fock (HF) calculation using the cc-pVDZ basis set. Note that there should be no `OPT` keyword, as we are performing a single-point calculation on this geometry. 

Make sure that you also change the `%chk=` keyword so it fits with the filename of the input file, for example:
```
%chk=L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz.chk
```
if you use the filename I suggested. 


You will now need to submit the calculation using the `g16` wrapper discussed in last lecture. I would suggest to use only 4 cores for the calculation (`-c 4`)

Once the calculation has finished, obtain the following information from the output file, either by opening with `vi` or by using GaussView:
- How many SCF iteration did it take to converge the HF calculation?
- What is the total energy of the molecule? (Important to note what the units are)
- What are the energies of the HOMO and LUMO?
- What is the HOMO-LUMO gap in eV?

## ORCA 6 - Hartree-Fock Calculations 

You should now do the same calculation with ORCA 6 code, another quantum chemistry code we will use throughout the course. 

A tutorial for ORCA 6 can be found [here](https://www.faccts.de/docs/orca/6.0/tutorials/index.html). We will be using this tutorial in the course. 

For today, we want to do a HF single-point calculation, which is discussed in [this tutorial](https://www.faccts.de/docs/orca/6.0/tutorials/prop/single_point.html). The first example in this tutorial shows how to do a HF calculation. 

Create an ORCA input file for doing a HF/cc-pvdz calculation on the same L-Tryptophan geometry as you did using Gaussian. I would suggest to use the filename `L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz_orca.inp` for the input file. 

The format of the input file should be something like this:
```
!HF cc-pvdz
* xyz 0 1
<INSERT XYZ COORDINATES HERE>
*
```

You can then submit the orca input file using the `orca` wrapper that works in similar way as the `g16` wrapper. The main difference is that you will need to specify the version; here we will use version 6.1.0 of ORCA that is the latest version.
```
orca -i L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz_orca.inp -p compchem.36 -c 4 -m 16gb -s local -v 6.1.0
```
You should check the output file that you are using the correct version 6.1.0. You can look at the molecular orbtials from the ORCA 6 calculation using the ChimeraX program that is started using the `ChimeraX`. 

Once the calculation has finished, obtain the following information from the output file:
- How many SCF iteration did it take to converge the HF calculation?
- What is the total energy of the molecule? (Important to note what the units are)
- What are the energies of the HOMO and LUMO?
- What is the HOMO-LUMO gap in eV?
- How does this compare to the Gaussian calculation?







