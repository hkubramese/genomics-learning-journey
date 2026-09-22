# Genomics Learning Journey

A structured, in-order record of my path into computational genomics —
from Python fundamentals through genomics theory to a working NGS pipeline
applied to real sequencing data.

## Structure

| Folder | What's in it |
|---|---|
| [`01-python-foundations`](./01-python-foundations) | Python for genomics — data types, functions, FASTA/FASTQ parsing, GC content, Biopython |
| [`02-bif101-genomics-fundamentals`](./02-bif101-genomics-fundamentals) | Core genomics concepts — sequencing technologies, raw data formats, QC, alignment, variant calling, visualization, cloud platforms |
| [`03-bif201-ngs-pipeline`](./03-bif201-ngs-pipeline) | A full hybrid short-read + long-read NGS pipeline (Illumina + Nanopore) applied to a bacterial genome — QC through variant calling |

## Why this order

Each folder builds on the one before it. Python foundations gave me the
tools to manipulate sequence data directly. BIF101 gave me the conceptual
map — what each step in an NGS workflow is actually doing and why. BIF201
is where those two things came together: a real pipeline, run on real
sequencing data, end to end.

## Background

This coursework follows a TÜBİTAK-funded research project on gene
expression analysis (KLF7), which is what pointed me toward computational
genomics in the first place. The BIF201 pipeline here is also the basis
for an independent project I'm currently developing — applying the same
pipeline to a new genome for further analysis.
