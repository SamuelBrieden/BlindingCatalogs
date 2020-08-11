# BlindingCatalogs

A repository of original and blinded galaxy catalog power spectrum measurements from BOSS DR12 data and Patchy Mocks and the corresponding BAO (pre- and post reconstruction) and RSD fit results.

It contains the most relevant results of the paper:
https://arxiv.org/abs/2006.10857

In that paper, all information about model parameters, priors, reference cosmology, fiducial blinding scheme, reconstruction scheme, etc can be found.

Blinded Patchy Mock and BOSS DR12 catalogs (having used the "Combined" case given in table 2 of the paper) are stored here in the tar.gz format:
https://drive.google.com/drive/folders/1SH-zEWSP28PoLUb7iHi97V0ALNg7roZi?usp=sharing

This archive also contains compressed versions of the Bestfits and Measurements presented here, as well as the full mcm chains.

The corresponding original catalogs and all their specifications (not changed for the blinded catalogs) can be found in:
Patchy Mocks: http://www.skiesanduniverses.org/Products/MockCatalogues/SDSS/
BOSS DR12: https://www.sdss.org/dr12/

The folder structure is as follows: On top level, there are the surveys (either BOSS data or Patchy Mocks), in the next level there are folders for either the original or the blinded cases. Then, there are folders corresponding to Measurements (either pre- or postreconstruction) and Bestfit files (either for BAO prerecon only for Patchy Mocks), BAO postrecon or RSD (full shape) fits). All files follow the naming convention "filespecifier_identifier", where "identifier" relates to the galaxy Sample used (LOWZ or CMASS) and other details depending on the configuration during the blinding, reconstruction and analysis steps. In the following you find an explanation of the different file types and their format. Units for wavevector k and power spectra Pk are always h/Mpc and Mpc^3/h^3 respectively


# Format specifications

## Measurements
These are all files starting with filespecifier="Power_Spectrum". They contain a LARGE header with ALL the relevant information on how the measurement has been obtained from the catalog. There are 9 columns corresponding to:
"k-centerbin	 k-eff	 Monopole-Pshotnoise	 Dipole	 Quadrupole	 Octopole	 Hexadecapole	 number of modes	 Pshotnoise"

## Bestfits
There are three different types of files for each fit: One starts with filespecifier="logfilemcmc" and contains information on mcmc runtime, number of steps convergence, and derived mean +/- sigma of each parameter as well, their bestfit value and the correlation matrix. The order of parameters is the same as in Table 3 of reference https://arxiv.org/abs/2006.10857. The Monopole and Quadrupole of the actual Bestfit models are plotted in files filespecifier="Monopole12" and filespecifier="Quadrupole12". The columns are:
"k 	 P_l(data) 	 1-sigma-error 	 P_l(model)"

## Chains (accessible via the Google Drive link above)
For BOSS DR12: filespecifier="mcmc<fittype>_output"
For Patchy Mocks: filespecifier="mcmc<fittype>_tail"
To save resources, for the Patchy Mock realizations I only include the last 10.000 points of each of the 6 chains (therefore named "tail"), while I include the full chains in the BOSS DR12 case. The columns are:
"mcmc-weight    chi^2    parameters" 

# Some more details
When going through the files you will see some parts in the names that have not been explained yet, here I present those parts of the identifiers to understand where the name comes from:
- "diffz": Means that the measurements on blinded catalogs were obtained using the "shifted redshift cuts" convention as suggested in the paper.
- "SameCovmat": Means that the same covariance matrix has been used on the blinded catalogs as for the original catalogs
- "withMask": Means that the survey window function has been applied
- "Gamma0825Smooth10": this indicates the blinding convention: Here the blinded ggrowth rate for each Sample has been obtained using a growth index of 0.825 and a smoothing scale of 10 Mpc/h.
- "f0784b1850s10": Appears for reconstructed mocks only. In this case the corresponding blinded catalog has been obtained with an input growth factor f=0.784, linear galaxy bias b=1.85 and smoothing scale s=10 Mpc/h.


Let me know if you have any questions:
sbrieden@icc.ub.edu

