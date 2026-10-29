# ChIP-seq Analysis Pipeline (Nextflow & Docker)

[![Nextflow](https://img.shields.io/badge/nextflow-%E2%89%A525.10.4-brightgreen.svg)](https://www.nextflow.io/)
[![docker](https://img.shields.io/badge/container-Docker-blue.svg)](https://www.docker.com/)
[![nf-core](https://img.shields.io/badge/nf--core-chipseq-orange.svg)](https://nf-co.re/chipseq)

## Overview
This repository contains a containerized, reproducible bioinformatics pipeline for processing and analyzing **Chromatin Immunoprecipitation Sequencing (ChIP-seq)** data. The pipeline identifies genome-wide DNA-protein interaction sites, histone modifications, and transcription factor binding events.

---

## Pipeline Architecture (`nf-core/chipseq`)
1. **Quality Control & Trimming**: FastQC and Trim Galore! for adapter removal and read quality verification.
2. **Alignment**: Mapping reads to the reference genome using **BWA** or **Bowtie2**.
3. **Filtering & Post-Processing**: Marking PCR duplicates and filtering low-quality or non-unique alignments using **SAMtools** and **Picard**.
4. **Peak Calling**: Identifying narrow or broad peaks relative to control samples using **MACS2**.
5. **Annotation & Quantification**: Annotating genomic features with **HOMER** and generating bigWig tracks for visualization in IGV.

---

## System Requirements & Execution
Optimized for local containerized execution on resource-constrained environments (e.g., 8 GB RAM laptop running WSL2/Docker) using a custom configuration (`laptop.config`).

### Quick Start (Test Profile)
```bash
nextflow run nf-core/chipseq \
  -profile test,docker \
  -c laptop.config \
  --outdir ./results
```
