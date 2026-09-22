
# BIF201 – Hybrid NGS Variant Calling Pipeline

A hands-on genomic data analysis pipeline built during the BIF201 course (DNA Academy, instructor Önder Akyün), applied to a real hybrid Illumina + Oxford Nanopore dataset from the *Gluconobacter cerinus* FLW-1 genome project. Published with the instructor's permission.

## Pipeline Overview

| Notebook | Content |
|---|---|
| `bif201-day2-qc-pipeline-setup.ipynb` | Downloading raw data from SRA/ENA, downsampling strategy, FastQC (short-read) and NanoPlot (long-read) quality control, combining reports with MultiQC |
| `bif201-day3-filtering-trimming-re-qc.ipynb` | Trimming and filtering with Cutadapt (Illumina) and Porechop + Filtlong (Nanopore/PacBio), followed by Re-QC to verify the cleanup |
| `bif201-day4-mapping-strategy.ipynb` | Paper-faithful filtering with Trimmomatic, downloading the real reference genome (NCBI accession JAFEJB010000000), installing BWA-MEM and Minimap2 |
| `bif201-day5-variant-calling.ipynb` | Full end-to-end pipeline: reference acquisition, BWA-MEM/Minimap2 alignment, BAM quality control, variant calling with BCFtools, and truth-VCF comparison (TP/FN/FP, sensitivity/precision) |

## Why This Order

The first three notebooks build the pipeline up in isolated stages — QC, then noise removal, then alignment setup — each verified before moving to the next. The last notebook (`bif201-day5-variant-calling.ipynb`) is the complete live-lesson pipeline: it goes from raw reference genome acquisition all the way through alignment, BAM QC, and variant calling, then evaluates the caller's output against a known truth VCF to measure real-world accuracy (true positives, false negatives, false positives).

## Technologies and Tools

- **Quality control:** FastQC, NanoPlot, MultiQC
- **Trimming / filtering:** Cutadapt, Trimmomatic, Porechop, Filtlong
- **Alignment:** BWA-MEM (short read), Minimap2 (long read)
- **Variant calling & comparison:** SAMtools, BCFtools

## Background

This pipeline was built on real public sequencing data (NCBI SRA/ENA accessions SRR13680736 and SRR13680735) referencing the *Gluconobacter cerinus* FLW-1 genome assembly (NCBI accession JAFEJB010000000). The methodology follows the reference paper's approach for combining short-read accuracy with long-read structural resolution in a hybrid assembly context.
