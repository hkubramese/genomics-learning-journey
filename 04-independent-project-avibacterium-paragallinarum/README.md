# Independent Project – Avibacterium paragallinarum Hybrid Pipeline

An independent application of the BIF201 hybrid Illumina + Oxford Nanopore pipeline to a different organism and dataset, built after completing the BIF201 course, to test whether the same workflow generalizes to a new genome.

## Reference Paper

Hashish et al. (2023). Complete genome sequences generated using hybrid Nanopore-Illumina assembly of two non-typical *Avibacterium paragallinarum* strains isolated from clinically normal chicken flocks. *Microbiology Resource Announcements*, 12(10): e00128-23. DOI: [10.1128/MRA.00128-23](https://doi.org/10.1128/MRA.00128-23)

## Organism

**Avibacterium paragallinarum** is a Gram-negative bacterium (family Pasteurellaceae) and the causative agent of infectious coryza, an acute respiratory disease in chickens. The strain used here (npAP/GA-USA/20231216/S1-1) was isolated from a healthy, clinically normal layer chicken in Georgia, USA in 2023.

**BioProject:** [PRJNA1177890](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA1177890)

## Sequencing Data

| Platform | SRR | Size |
|---|---|---|
| Illumina MiSeq (Paired-End) | SRR31123925 | 710.6 MB |
| Oxford Nanopore MinION (Single-End) | SRR31139160 | 1,019.9 MB |

## What This Notebook Covers

`avibacterium-paragallinarum-pipeline.ipynb` applies the same pipeline structure used in the BIF201 course (`03-BIF201-ngs-pipeline`) to this independent dataset:

1. Subsampling 50,000 reads per platform directly from NCBI SRA
2. Quality control with FastQC (Illumina), NanoPlot (Nanopore), and MultiQC (combined)
3. Trimming and filtering with Cutadapt (Illumina) and NanoFilt (Nanopore)
4. Re-QC to verify the cleanup worked, and a comparison of tool/parameter choices against the reference paper's methodology (adapter kit, trimming tool, Filtlong parameters)
5. Downloading the full (non-subsampled) raw datasets

**Genome assembly (Unicycler) is not yet completed** — it's outlined conceptually in the notebook as the next step, but wasn't run to completion in this pass. Adding a full hybrid assembly and evaluating it against the reference paper's reported genome stats is a natural next step for this project.

## Reports

| File | What it is |
|---|---|
| `SRR31123925_1_fastqc.html`, `SRR31123925_2_fastqc.html` | FastQC reports for the Illumina forward/reverse reads |
| `NanoPlot-report.html` | NanoPlot report for the Nanopore reads |
| `multiqc_report.html` | Combined QC report (raw/subsampled data) |
| `multiqc_report_filtered.html` | Combined QC report after trimming and filtering |
| `SRR13680736_1_fastqc_reference.html`, `SRR13680736_2_fastqc_reference.html` | FastQC reports from the BIF201 course's own Gluconobacter cerinus dataset, kept here for side-by-side comparison |

## Why This Matters

The BIF201 course pipeline (in `03-BIF201-ngs-pipeline`) was applied to *Gluconobacter cerinus*, using tools and parameters matched to that specific reference paper. This project checks whether the same overall approach holds up on an unrelated bacterium with a different adapter kit (Nextera XT vs. NEBNext Ultra II) and a different reference paper's methodology — a first step toward being able to apply this pipeline to any new bacterial genome project.
