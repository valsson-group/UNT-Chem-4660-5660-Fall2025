# Lecture 7 - Vibrational Frequency Calculations 

September 16, 2025

In today's hands-on, we are going to set up frequency calculations for [Ethylene](https://pubchem.ncbi.nlm.nih.gov/compound/Ethylene), both for Gaussian and ORCA

### Vibrational Frequency Calculations for Ethylene

You should set up vibrational frequency calculations for Ethylene, both using Gaussian and ORCA. 

It would be best if you do not use GaussView to set up the calculations, only a text editor (e.g., `vi`) on cruntch4. 

Use the initial geometry that is available on cruntch4 at the following path:
```
/storage/nas_scr/shared/groups/compchem-chem5600/Lectures-2025/Lecture-7_Sept-16-2025/Ethylene-Initial-MMFF94.xyz
```
You should use the B3LYP-D3 with the cc-pVDZ basis set for the calculations.

You should perform a geometrical optimization followed by a vibrational frequency calculation at the ground state minimum. The relevant keywords are:
- Gaussian: `OPT(Tight) FREQ`
- ORCA: `OPT FREQ TIGHTOPT`

You should use ORCA 6.1 for the calculations by using the `-v 6.1.0 flag` in the ORCA submission wrapper. 

For the Gaussian calculation, you can open the log file (or checkpoint file) using GaussView and visualize the normal modes, and obtain the IR spectrum (which can be output to a file). This will be shown in class. 

For the ORCA calculations, you can open the output file with ChimeraX or Avagadro and visualize the normal modes and obtain the IR spectrum. This will be shown in class. 

### Obtaining IR spectrum from ORCA calculations 

For ORCA, you can also obtain the IR spectrum using the `orca_mapspc` command line tool; see ORCA 6.1 [manual]([https://www.faccts.de/docs/orca/6.0/manual/contents/typical/properties.html#ir-raman-spectra-vibrational-modes-and-isotope-shifts](https://www.faccts.de/docs/orca/6.1/manual/contents/spectroscopyproperties/vibrations.html#sec-spectroscopyproperties-vib-ir))

To be able to use the `orca_mapspc` tool, you must load the `ORCA/6.1.0_avx2` module on cruntch4:
```
module load ORCA/6.1.0_avx2
```
Then you use it in the following way:
```
orca_mapspc <FILENAME>.out ir -w25
```
Where `-w25` is a linewidth parameter that controls the broadening of each peak (done with a Gaussian kernel). This will result in a data file with the filename `<FILENAME>.out.ir.dat` that you can plot. By default, the spectrum will be in inverse centimeters and will be given in terms of transmittance. 

### Vibrational Frequency Calculations -- The Wrong Way

Try to perform a vibrational frequency calculation without doing a geometrical optimization, that is, using the following keywords:
- Gaussian: `FREQ`
- ORCA: `FREQ`
(Without any `OPT` or `TIGHTOPT` keywords)

What happens in this case? How can you see that this calculation is wrong? 









