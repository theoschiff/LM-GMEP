# Goal
Predict Pathogenic vs Benign mutations from sequence alone (i.e not using clinical info)

## Method
Trained and evaluated state-of-the-art language models and analysed results.

## Dataset
70 Cancer genes from [ClinVar](https://www.ncbi.nlm.nih.gov/clinvar/) 
<br>
*hgvs4variation_filtered.csv* contains GeneID with AlleleID , wildtype sequence and nucleotide expression after variation <br>
*variant_summary_filtered.csv* contains the clinical signifance for many single mutations of the selected gene <br>

## Cleaning and transformations
Applied several filters to the data:
>Removed all stop codon mutations & no amino acid change mutations <br>
Truncated proteins to under 1022 amino acids for model compatibility<br>
Removed mutations where wild type did not correspond in sequence<br>
Removed samples without clinical significance info

## Big picture
![bigpicturegenes](https://user-images.githubusercontent.com/73180998/233119220-301c38e9-6f27-4b8a-9301-753e7d055e6c.png)
<br>

In total: 
66455 VUSs<br>
1195 Benign<br>
1800 Pathogenic

~ 3K data points for evaluation


## Format
Everything is contained in jupyter notebooks, including visualisation, validation and training.

## Models
Copyright (c) Facebook, Inc. and its affiliates. <br>
Deborah Marks' group 

**ESM-1v**: Published by Meta, trained as a masked language model on millions of proteins <br>
https://www.biorxiv.org/content/10.1101/2021.07.09.450648v2.full 

**EVE**: Published by Deborah Marks’s group, also MSA based, claims > 90 AUC on ClinVar<br>
https://www.nature.com/articles/s41586-021-04043-8#Abs1

**ESM-1F**: Inverse-Folding model (predict sequence from structure), uses 3D protein structure generated from *AlphaFold2* Model<br>
https://www.nature.com/articles/s41586-021-04043-8#Abs1

## Results 
Achieved 0.85 AUC by combining inverse folding model and EVE model.
## Analysis
While the inverse folding performs worse than the other two, we note that it outperforms the best model EVE on  14 / 70 genes highlighting the potential power of combining MSA & structure based approached.

Is this a function of the quality of the 3D structure?<br>
>It doesn't seem so. 

SpearmannR = 0.1, meaning that there is no correlation between the per-residue confidence score of the protein structure and the AUC.

### Note
The code is somewhat unorganised and is far from optimal.
