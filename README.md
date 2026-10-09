# aLb2_ICAM1_dms
Deep mutational scanning of the alpha L I domain and TiteSeq with ICAM-1

This repo contains documentation needed to analyze the deep mutational scanning TiteSeq data for the alphaL I domain. Briefly, this project utilized a pooled yeast display assay to determine how genetic variation affects the affinity of the alphaL I domain for its cognate ligand, ICAM-1. This protocol is based on foundational work performed in Adams et al. 2016 (https://pubmed.ncbi.nlm.nih.gov/28035901/) and Starr et al. 2020 (https://pubmed.ncbi.nlm.nih.gov/32841599/), which explain concepts of the assay in great detail. These analyses were run on a combination of local computing, the Campbell Lab cluster and the Fred Hutch Cancer Center computational cluster.

# Workflow

The raw sequencing data were analyzed in 3 major steps:
1) Link N16 barcodes to genetic variants via long read PacBio sequencing via the conda notebook aL_Idom_DMS_CCSparse.ipynb. This creates a codon variant lookup table (codon_variant_table_aLIHA.csv).
2) Create a count distribution by parsing illumina barcodes to variants using count_variants.ipynb. This depends on having the correct data/barcode_runs.csv file, which points to both where data are stored and to how many cells were sorted into each bin. 
3) Determine binding affinities from the distribution of barcode sequences across titrations from the TiteSeq FACS and illumina sequencing experiment. This is done in R via the notebook binding_kd_calc_final.Rmd. Collapse affinity scores and generate plots for publication via collapsescoresICAM1_bindonly.Rmd. This also produces dtfinal.csv which contains both raw and normalized changes in affinity for each biological replicate.
