# Lecture 9 - Vibrational Frequency Calculations 

September 23, 2025

In today's hands-on, we are going to work on analyzing results from vibrational frequency calculations for Assignment 2

### Obtaining IR Spectrum from Gaussian Calculations 

For Gaussian 16, you can obtain the IR spectrum using GaussView, as was shown in Lecture 8. This allows you to obtan a data text file that you can plot. 


### Obtaining IR Spectrum from ORCA Calculations 

For ORCA, you can obtain the IR spectrum using the `orca_mapspc` command line tool; see ORCA 6.1 [manual](https://www.faccts.de/docs/orca/6.1/manual/contents/spectroscopyproperties/vibrations.html#sec-spectroscopyproperties-vib-ir)

To be able to use the `orca_mapspc` tool, you must load the `ORCA/6.1.0_avx2` module on cruntch4:
```
module load ORCA/6.1.0_avx2
```
Then you use it in the following way:
```
orca_mapspc <FILENAME>.out ir -w25
```
Where `-w25` is a linewidth parameter that controls the broadening of each peak (done with a Gaussian kernel). This will result in a data file with the filename `<FILENAME>.out.ir.dat` that you can plot. By default, the spectrum will be in inverse centimeters and will be given in terms of transmittance. 

### Plotting and Comparing IR Spectrum to Experiments

One of the files you are given in Assignment 2 is the experimental IR spectrum, given in absorbance as a function of wavenumber (cm<sup>-1</sup>). Depending on the code used, you will either get the IR spectrum in terms of absorbance or transmittance. Therefore, you will need to manipulate the data to be able to compare two or more spectra on the same plot. The following Jupyter notebook shows how to do this:

[Manipulation of Data and Plotting It Using Using Python](https://colab.research.google.com/github/valsson-group/UNT-Chem-4660-5660-Fall2025/blob/main/Python-Plot-IR-Spectrum/Plot_IR_Spectra.ipynb)








