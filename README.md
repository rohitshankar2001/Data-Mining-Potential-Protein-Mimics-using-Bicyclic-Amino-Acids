# Data-Mining-Potential-Protein-Mimics-using-Bicyclic-Amino-Acids
# Project Steps
1. Create SMILES library using induced backbone matching with benzylic tribromide + peptide chain + thiol. 
2. Use Monte Carlo Multiple Minimum for conformational sampling via Schrodinger Maestro. 
3. Modify format of MCMM output to match Protein Data Bank 
4. Overlay cyclic peptides with protein backbones. Find low RMSD values.

# Step 1: Creating Bicyclic SMILES library
The SMILES library is composed of 640 bicyclic amino acids chains of lengths from 1 to 10. The python script creates the 640 bicyclic amino acids by combining each pool of possible molecules to create 640 unique potential mimics.<br>
The bicyclic amino acids follow the pattern of cysteine-alanine(1-10)-cysteine-alanine(3-10)-cysteine. The amino acid chain is held together with a tribromide benzylic which connects to each thiol of the cysteine. 
<img src="https://user-images.githubusercontent.com/115378538/210922971-8e905daf-ad95-4d91-ad5d-620a865d9146.png" width="900" height="400">

Below are some bicyclic amino acids created by the script created:<br>
<img src="https://user-images.githubusercontent.com/115378538/210923358-78b2a234-9f76-4578-8c06-6c3dc99ffddc.png" width="450" height="200">
<img src="https://user-images.githubusercontent.com/115378538/210923789-daead1cd-9b19-4f59-a679-9c368226f71a.png" width="400" height="200">

# Step 2: Conformational Sampling using Schrodinger Maestro
Each SMILES file of the 640 bicyclic amino acids was placed into Maestro with the intent to collect conformers. The goal of conformational sampling was to obtain mol2 files which describe different orientations the bicyclic amino acid could be given specific settings. More information about settings can be found in the conformational sampling folder. <br>
<br>
Example of 3d conformer generated from conformational sampling: <br>

<img src="https://user-images.githubusercontent.com/115378538/210926145-c1bd356b-073f-4a49-b5fa-84b14d2eafe6.png" width=40% height=auto>

# Step 3: File modification from mol2 to pdb
For the next step to work correctly, each conformer mol2 file needs to be converted to the protein data bank file type. This involves iterating through all the conformers and altering residue and atom ID to match that of the pdb file type. More information can be found in the folder

# Step 4: Overlay of conformers with protein to test possibility of mimic
Each conformer is overlayed using the pymol library align function. The align function returns the RMSD of the conformer when overlayed with a given protein. In the folder the protein Urease and GDNF are tested to find good overlays. The best overlay for GDNF yielded a RMSD of roughly 2. Further testing is required to see if bicyclic peptide could be a mimic. <br>
Below is example of an alignment:
![image](https://user-images.githubusercontent.com/115378538/211127847-4ff5c707-b12d-416c-b5db-56884e4f0041.png)

