# PheWAS in collectively selected genomic regions in the Andean and Nepali highlanders







## Analysis Plan:



### Run iSAFE on the Andean and Nepali genome

From google drive download the Andean and Nepali iSAFE stats: 

[Andean iSAFE download]([https://drive.google.com/file/d/1WlEtl6IwZhPVdzxg00OtzwjnZN156cr7/view?usp=sharing](https://drive.google.com/file/d/1WlEtl6IwZhPVdzxg00OtzwjnZN156cr7/view?usp=sharing))

[Nepali iSAFE download]([https://drive.google.com/file/d/1kws_OKlMxL3xuekXGVh2N2zVGSYWzvDm/view?usp=sharing](https://drive.google.com/file/d/1kws_OKlMxL3xuekXGVh2N2zVGSYWzvDm/view?usp=sharing))



Get tables like this:

| CHR  | POS   | VARIANT | iSAFE      | DAF    |
| ---- | ----- | ------- | ---------- | ------ |
| 1    | 52058 | 1_52058 | 0.0087625  | 0.1    |
| 1    | 52727 | 1_52727 | 0.00433923 | 0.075  |
| 1    | 55085 | 1_55085 | 0.01035339 | 0.1    |
| 1    | 56638 | 1_56638 | 0.00656669 | 0.1125 |
| 1    | 57856 | 1_57856 | 0.01187717 | 0.325  |
| 1    | 57999 | 1_57999 | 0.00201494 | 0.0875 |

where CHR, POS are chromosome and positions, VARIANT is chr_pos, iSAFE is a score in between 0 and 1, and DAF is the delta allele frequency of the variant between the target population and the reference population (X1000).



### Test for collectively selected genomic regions in the two highlanders genomes

1. Overlap the signals
   1. Group variants that are close enough to each other in both populations (distance ≤ 200mb). If multiple variants are present in the same 200 mb window, keep all of them.
   2. Check the LD between the two variants in the world (this is not the best practice but it should be fastest way to do it. We will definitely use a better approach later) The LD between the two variants can be checked very quickly using LDlink - LDpop ([https://ldlink.nci.nih.gov/?tab=ldpop](https://ldlink.nci.nih.gov/?tab=ldpop)). For population, select ALL.
2. Calculate compound iSAFE score 
   1. Compound iSAFE score = (Andean iSAFE * Nepali iSAFE)^0.5
3. Rank the regions based on the compound iSAFE score
4. Threshold the regions/variants based on the compound iSAFE score (compound iSAFE ≥ 0.1)
5. Annotate the regions with high compound iSAFE score



### Examine the genes/variants with high compound iSAFE score



1. Save the plot from UCSC genome browser ([https://genome.ucsc.edu/](https://genome.ucsc.edu/))
2. Investigate the function of the genes via Gene Card ([https://www.genecards.org/](https://www.genecards.org/))
3. Look up PheWAS results from hugemap ([https://hugeamp.org/](https://hugeamp.org/))
4. Look up GWAS results from GWAS catalog ([https://www.ebi.ac.uk/gwas/](https://www.ebi.ac.uk/gwas/))



### Summarize the results



**Create a master excel file with a few different tabs (sheets): **

1. All Nepali variants with iSAFE score greater than or equal to 0.1
2. All Andean variants with iSAFE score greater than or equal to 0.1
3. All variants (Nepali + Andean) with compound iSAFE score greater than or equal to 0.1
4. All variants from sheet3 annotated with which gene they are from, and what are these genes known for (from Gene Card). Additionally, add significant associations identified in HugeMap and in GWAS catalog.



### Visualization

1. Manhattan plot for the Nepali and Andean populations
2. Manhattan plot for the compound iSAFE score
3. Locuszoom plots of top selected regions in both populations (individually and collectively)
4. PheWAS plot from HugeMap.