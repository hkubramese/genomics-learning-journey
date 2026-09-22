[README_bif101.md](https://github.com/user-attachments/files/32509580/README_bif101.md)
# BIF101 – Genomics Fundamentals

A summary of the core concepts and tools covered in this module: the history of sequencing technologies, raw sequencing data formats, quality control, alignment, variant detection, and visualization — the conceptual foundation the NGS pipeline work in `03-bif201-ngs-pipeline` builds on.

## Why This Module Mattered

Before running any pipeline, it's important to understand what each step in a genomic analysis actually does and why it's needed — not just which command to type. This module covers the full path from raw sequencing reads to an annotated, visualized result, and the reasoning behind each stage.

## History of Sequencing

- **Sanger sequencing** — the first widely used method, accurate but low-throughput and expensive for large-scale work.
- **Next-Generation Sequencing (NGS)** — massively parallel short-read sequencing (e.g. Illumina), which made whole-genome and population-scale sequencing practical by drastically increasing throughput and lowering cost.
- **Long-read sequencing** — platforms like Nanopore and PacBio, which trade some per-base accuracy for much longer reads, making it possible to resolve repetitive regions and structural variants that short reads struggle with.

## Raw Sequencing Data

- **FASTQ format** — each read is stored as 4 lines: an identifier, the sequence itself, a separator, and a per-base quality score (Phred score) line.
- **Platform-specific characteristics:**
  - *Illumina* — short reads, high per-base accuracy, substitution-dominated errors.
  - *Ion Torrent* — semiconductor-based sequencing, prone to indel errors especially in homopolymer regions.
  - *Nanopore* — long reads via a physical pore, historically higher error rates (mainly indels), improving with newer chemistry/basecalling.

## Quality Control and Filtering

Raw reads are checked and cleaned before any downstream analysis:

- **FastQC** — standard QC report tool for short reads (per-base quality, GC content, adapter contamination, overrepresented sequences).
- **NanoPlot / LongReadSum** — QC summary and plotting tools for long-read data.
- **Filtlong** — filters long reads by length and quality.
- **Porechop** — trims adapters from Nanopore reads.
- **Sequali** — general-purpose QC tool for both short and long reads.
- **seqQscorer** — machine-learning based tool that predicts sequencing quality issues from QC metrics.

## Alignment and Mapping

Once reads are cleaned, they're mapped to a reference genome:

- **BWA** — widely used short-read aligner, particularly BWA-MEM for reads over ~70bp.
- **Bowtie2** — another fast, memory-efficient short-read aligner.
- **NovoAlign** — commercial aligner known for high accuracy.
- **Minimap2** — versatile aligner that handles both long reads and short reads, and is the standard choice for Nanopore/PacBio data.
- **Graph-based alignment (e.g. GraphAligner)** — aligns reads against a graph-structured reference (a pangenome) instead of a single linear sequence, which better represents genetic variation across individuals.
- **GATK preprocessing** — steps like duplicate marking and base quality score recalibration (BQSR) that clean up alignments before variant calling.

## Variant Detection and Annotation

- **GATK HaplotypeCaller** — calls SNPs and small indels by locally reassembling haplotypes around candidate variant regions.
- **SAMtools / BCFtools** — used for manipulating alignment files (SAM/BAM) and calling/filtering variants (VCF).
- **FreeBayes** — a Bayesian variant caller that also works well for small indels and low-frequency variants.
- **DeepVariant** — a deep-learning based variant caller that treats variant calling as an image classification problem.
- **Annotation (VEP, ANNOVAR, SnpEff)** — once variants are called, these tools annotate them with functional consequences (e.g. missense, nonsense, intronic), affected genes, and known clinical significance.

## Visualization and Reporting

- **UCSC Genome Browser / Ensembl** — web-based genome browsers for exploring reference annotations and public datasets.
- **IGV (Integrative Genomics Viewer) / JBrowse2** — desktop/web tools for visually inspecting alignments and variants directly against the reference genome.
- **R Markdown / Jupyter Notebook** — used to combine code, results, and narrative into a single reproducible analysis report.
- **cBioPortal / UCSC Xena** — platforms for exploring and visualizing large public cancer genomics and multi-omics datasets.

## Cloud Platforms

- **Galaxy Project** — a web-based platform that lets you build and run bioinformatics pipelines through a graphical interface, without needing to manage the command line or software installations directly.
- **Galaxy Training Network (GTN)** — a large collection of structured tutorials for learning bioinformatics workflows on the Galaxy platform.

## General Workflow

The overall shape of a genomic analysis, regardless of the specific tools used:

1. **Data collection** — raw sequencing reads (FASTQ) from the relevant platform.
2. **Quality control** — checking and cleaning the raw reads.
3. **Alignment / preprocessing** — mapping reads to a reference genome and preparing the alignment for variant calling.
4. **Variant detection** — identifying SNPs, indels, and other variants, followed by annotation.
5. **Visualization / reporting** — inspecting and communicating the results.

## Connection to BIF201

The pipeline built in `03-bif201-ngs-pipeline` applies this exact workflow — QC, alignment, variant detection, and reporting — to a real hybrid Illumina + Nanopore dataset, combining the accuracy of short reads with the structural resolving power of long reads.
