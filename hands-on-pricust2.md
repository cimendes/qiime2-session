---
title: "Hands-on: Prediction of functional diveristy using 16S rRNA gene data with Picrust2"
author: "Belen Carbonetto"
date: "November 2018"
Version 3
output: html_document
---

## Prediction of functional diveristy using DADA2 output files and Picrust2

### Learning outcomes:

**During this hands-on session you will learn how to:**

Use DADA2 output to infer [EC](https://bitesizebio.com/10683/understand-ec-numbers-in-5-minutes-part-i-how-ec-numbers-work/) numbers and [KO](https://www.genome.jp/kegg/ko.html) predictions. 

MetaCyc pathway coverages and abundances will also be calculated and .tsv files with results will be exported.

**Notes:** Picrust2 and the plugin *q2 picrust2* has already been installed in your working station in order to follow this tutorial.
If you are following the tutorial on your own please find instructions for the installation [here](https://library.qiime2.org/plugins/q2-picrust2/13/)

This tutorial is ment to be followed after the QIIME2-sessions [hands-on](https://github.com/mbcarbonetto/qiime2-session/blob/master/Hands-on-V3.md)

- Every task that you will perfom is marked with &#x1F536;

- Questions to further analyse results will be marked with :question:

### 0. Data set and input files

&#x1F536; You will need to download the reference files we will use in this session from this [link](https://github.com/mbcarbonetto/qiime2-session/tree/master/picrust). Please download both files:*reference.fna.qza* and * 	reference.tre.qza*.

The input files will be the output files from **qiime dada2 denoise-single**:the "feature table" artifact and the "representative sequence" artifact (i.e. table-dada2.qzv and representative_sequences.qza)

### 1. Place the ASVs against the PICRUSt2 reference multiple-sequence alignment and phylogeny.

The input files of this step are the representive sequences (i.e. the ASVs) and the refence tree and alignment.

Hint: It may be helpful to create a working directory for this step and copy all input files there, alternatively you can call the complete path for each file. Please note the paths maybe different to the paths is this tutorial

&#x1F536;

    mkdir picrust2_results
    mv Donwloads/reference.fna.qza picrust2/
    mv Donwloads/reference.tre.qza picrust2/
    
    qiime fragment-insertion sepp \
    --i-representative-sequences DADA2/representative_sequences.qza \
    --p-threads 1 \
    --i-reference-alignment picrust2/reference.fna.qza \
    --i-reference-phylogeny picrust2/reference.tre.qza \
    --output-dir picrust2/results
 
### 1. Run the full PICRUSt2 pipeline



