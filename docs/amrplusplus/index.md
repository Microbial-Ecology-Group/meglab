---
template: amrplusplus.html
title: AMR++ Pipeline
---

# AMR++ Bioinformatic Pipeline

AMR++ is a bioinformatic pipeline meant to aid in the high-throughput analysis of raw metagenomic sequencing reads to characterize the profile of antimicrobial resistance genes, or resistome. AMR++ was developed to work in conjuction with the the MEGARes database and the accompanying annotation structure that is optimized for use with high throughput analysis of metagenomic sequencing data. The acyclical annotation graph of MEGARes allows for accurate, count-based, hierarchical statistical analysis of resistance at the population level, much like microbiome analysis, and is also designed to be used as a training database for the creation of statistical classifiers.

MEGARes 3.0 contains sequence data for nearly 9,000 hand-curated antimicrobial resistance genes, and AMR++ v3.0 adds a new feature for high-throughput verification of resistance-conferring SNPs in relevant gene accessions (ARGs). 

The goal of many metagenomics studies is to characterize the content and relative abundance of sequences of interest from the DNA of a given sample or set of samples. You may want to know what is contained within your sample or how abundant a given sequence is relative to another.

Often, metagenomic analyses are performed when the answer to these questions must be obtained for a large number of targets where techniques like multiplex PCR and other targeted methods would be too cumbersome to perform. AMR++ can process the raw data from the sequencer, identify the fragments of DNA, and count them. It also provides a count of the polymorphisms that occur in each DNA fragment with respect to the reference database.

Additionally, you may want to know if the depth of your sequencing (how many reads you obtain that are on target) is high enough to identify rare organisms (organisms with low abundance relative to others) in your population. This is referred to as rarefaction and is calculated by randomly subsampling your sequence data at intervals between 0% and 100% in order to determine how many targets are found at each depth.

With AMR++, you will obtain alignment count files for each sample that are combined into a count matrix that can be analyzed using any statistical and mathematical techniques that can operate on a matrix of observations.
