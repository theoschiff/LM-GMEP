# Goal
Predict Pathogenic vs Benign mutations from sequence alone  (i.e not using clinical info)

# Dataset
70 Cancer genes from ClinVar: https://www.ncbi.nlm.nih.gov/clinvar/ 

## Cleaning and transformations
Applied several filters to the data:
>Removed all stop codon mutations & no amino acid change mutations <br>
Truncated proteins to under 1022 amino acids for model compatibility<br>
Removed mutations where wild type did not correspond in sequence<br>
Removed samples without clinical significance info

## Big picture
![bigpicturegenes](https://user-images.githubusercontent.com/73180998/233119220-301c38e9-6f27-4b8a-9301-753e7d055e6c.png)

# Format
Everything is contained in jupyter notebooks, including visualisation, validation and training.


## Results 


### Note
The code is somewhat unorganised and is far from optimal.
