# Lecture 3 - Hartree-Fock calculations 

September 2, 2025 

Unfortunately, cruntch4 is still not available for job submission, so we cannot perform calculations. 

Instead, we will consider results from calculations for L-Tryptophan performed previously in last year's course. 

You are supposed to analyze the Gaussian 16 and ORCA 6 output files. 

All the files can be found at the following link on cruntch4:
```
/storage/nas_scr/shared/groups/compchem-chem5600/Lectures-2025/Lecture-3_September-2-2025
```

You should copy this folder to the `Runs` folder in your home folder by using the `cp` command (see [Lecture 1](https://github.com/valsson-group/UNT-Chem-4660-5660-Fall2025/tree/main/Lectures-HandsOn/Lecture-1_August-26-2025) for the appropriate usage of the `cp` command when copying folders). 

## Gaussian 16 - Hartree-Fock Calculations 

The Gaussian 16 output files have the filenames `L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz.*`. 

Using `vi` or by using GaussView (started by using the `gv6` command), find the following information:
- Which exact version of Gaussian 16 are you using? (It should be denoted as `Rev` something).
- How many SCF iterations did it take to converge the HF calculation?
- What is the total energy of the molecule? (Important to note what the units are)
- How is the total energy split into nuclear repulsion energy and electronic energy?
- How many electrons does the molecule have? 
- What is the orbital number of the HOMO and LUMO?
- What are the energies of the HOMO and LUMO?
- What is the HOMO-LUMO gap in eV?

Using GaussView (started by using the `gv6` command), visualize the molecular orbitals (remember you need to load the correct file to be able to see the molecular orbitals). Save a picture of the HOMO and LUMO (using the "Save Picture" option). 

## ORCA 6 - Hartree-Fock Calculations 

The ORCA 6 output files have the filenames `L-Tryptophan_hf_cc-pvdz_geo_b3lyp_cc-pvdz_orca.*`. 

Once the calculation has finished, obtain the following information from the output file:
- Which exact version of ORCA are you using?
- How many SCF iterations did it take to converge the HF calculation?
- What is the total energy of the molecule? (Important to note what the units are)
- How is the total energy split into nuclear repulsion energy and electronic energy?
- How many electrons does the molecule have? 
- What is the orbital number of the HOMO and LUMO?
- What are the energies of the HOMO and LUMO?
- What is the HOMO-LUMO gap in eV?
- How does this compare to the Gaussian 16 results? 






