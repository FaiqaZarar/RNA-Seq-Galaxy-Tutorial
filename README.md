# Reference-based RNA-Seq Data Analysis

[![Platform](https://img.shields.io/badge/Platform-Galaxy%20Europe-blue?style=flat-square)](https://usegalaxy.eu/)
[![Organism](https://img.shields.io/badge/Organism-D.%20melanogaster-orange?style=flat-square)](https://www.flybase.org/)
[![Genome](https://img.shields.io/badge/Genome-dm6-green?style=flat-square)](https://www.ncbi.nlm.nih.gov/)
[![Pipeline](https://img.shields.io/badge/Pipeline-STAR%20%7C%20featureCounts%20%7C%20DESeq2-purple?style=flat-square)](https://training.galaxyproject.org/)
[![License](https://img.shields.io/badge/License-CC--BY--4.0-lightgrey?style=flat-square)](https://creativecommons.org/licenses/by/4.0/)

**Author:** Faiqa Zarar Noor
**NUST ID:** 471543
**Institution:** NUST — National University of Sciences and Technology
**Course:** BI-436: Special Topics in Bioinformatics
**Semester:** Spring 2026
**Date:** April 2026

---

## Abstract

This repository documents a complete reference-based RNA-Seq data analysis pipeline executed on Galaxy Europe, following the Galaxy Training Network tutorial for reference-based RNA-Seq analysis. The dataset consists of paired-end and single-end Illumina RNA-Seq reads from *Drosophila melanogaster* samples, comparing treated (Pasilla gene knockdown) versus untreated conditions. The pipeline covers five major stages: (1) quality control using Falco and MultiQC, (2) read trimming with Cutadapt, (3) spliced alignment to the dm6 reference genome using RNA STAR with visualization in IGV, JBrowse2, and strand-specific coverage plots, (4) gene-level read counting with featureCounts, and (5) differential gene expression analysis using DESeq2, producing PCA plots, sample-to-sample distance heatmaps, MA plots, and normalized count tables. A total of 7 samples (3 treated, 4 untreated) were analyzed, and the results confirm successful knockdown of the Pasilla gene.

**Keywords:** RNA-Seq, differential gene expression, DESeq2, STAR, featureCounts, *Drosophila melanogaster*, Pasilla, Galaxy, spliced alignment, PCA, heatmap

---

## Table of Contents

1. [Repository Structure](#1-repository-structure)
2. [Dataset](#2-dataset)
3. [Pipeline Overview](#3-pipeline-overview)
4. [Section 1 — Quality Control](#4-section-1--quality-control)
5. [Section 2 — Alignment](#5-section-2--alignment)
6. [Section 3 — STAR Coverage Strands](#6-section-3--star-coverage-strands)
7. [Section 4 — Gene Counting](#7-section-4--gene-counting)
8. [Section 5 — Differential Expression](#8-section-5--differential-expression)
9. [References](#9-references)

---

## 1. Repository Structure

```
RNA-Seq-Galaxy-Tutorial/
│
├── README.md                              ← This document
│
├── 01_quality_control/
│   ├── README.md                          ← QC methods and results
│   └── outputs/
│       ├── multiqc_raw_reads_report.html
│       ├── multiqc_after_trimming_report.html
│       └── falco_webpage.html
│
├── 02_alignment/
│   ├── README.md                          ← Alignment methods and results
│   └── outputs/
│       ├── jbrowse2_alignments_chr4.png
│       └── multiqc_star_alignment_report.html
│
├── 03_star_coverage/
│   ├── README.md                          ← STAR coverage strand visualization
│   └── outputs/
│       └── jbrowse_strand1_blue_strand2_red.png
│
├── 04_gene_counting/
│   ├── README.md                          ← featureCounts methods and results
│   └── outputs/
│       └── featurecounts_summary.tabular
│
└── 05_differential_expression/
    ├── README.md                          ← DESeq2 methods and results
    └── outputs/
        ├── deseq2_plots.pdf
        ├── deseq2_results.tabular
        └── deseq2_normalized_counts.tabular
```

---

## 2. Dataset

| Sample | Condition | Sequencing Type | GEO Accession |
|---|---|---|---|
| GSM461176 | Untreated | Single-end | GSM461176 |
| GSM461177 | Untreated | Paired-end | GSM461177 |
| GSM461178 | Untreated | Paired-end | GSM461178 |
| GSM461179 | Treated | Single-end | GSM461179 |
| GSM461180 | Treated | Paired-end | GSM461180 |
| GSM461181 | Treated | Paired-end | GSM461181 |
| GSM461182 | Untreated | Single-end | GSM461182 |

**Reference genome:** *Drosophila melanogaster* dm6
**Annotation:** Ensembl BDGP6.87 GTF
**Data source:** https://zenodo.org/record/6457007

---

## 3. Pipeline Overview

```
Raw FASTQ reads
      │
      ▼
┌─────────────────┐
│  Quality Control │  Falco + MultiQC
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│    Trimming      │  Cutadapt
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Alignment      │  RNA STAR → dm6
│   Visualization  │  IGV + JBrowse2
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ STAR Coverage    │  Strand 1 (blue) + Strand 2 (red)
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Gene Counting   │  featureCounts
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  DESeq2 Analysis │  PCA + Heatmap + MA plot
└────────┬────────┘
         │
         ▼
Differentially Expressed Genes
```

---

## 4. Section 1 — Quality Control

➡️ [View Section 1 README](./01_quality_control/README.md)

---

## 5. Section 2 — Alignment

➡️ [View Section 2 README](./02_alignment/README.md)

---

## 6. Section 3 — STAR Coverage Strands

➡️ [View Section 3 README](./03_star_coverage/README.md)

---

## 7. Section 4 — Gene Counting

➡️ [View Section 4 README](./04_gene_counting/README.md)

---

## 8. Section 5 — Differential Expression

➡️ [View Section 5 README](./05_differential_expression/README.md)

---

## 9. References

1. Batut, B., et al. (2018). Reference-based RNA-Seq data analysis. Galaxy Training Network. https://training.galaxyproject.org/training-material/topics/transcriptomics/tutorials/ref-based/tutorial.html
2. Dobin, A., et al. (2013). STAR: ultrafast universal RNA-seq aligner. *Bioinformatics*, 29(1), 15–21. https://doi.org/10.1093/bioinformatics/bts635
3. Liao, Y., Smyth, G. K., & Shi, W. (2014). featureCounts: an efficient general purpose program for assigning sequence reads to genomic features. *Bioinformatics*, 30(7), 923–930. https://doi.org/10.1093/bioinformatics/btt656
4. Love, M. I., Huber, W., & Anders, S. (2014). Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. *Genome Biology*, 15, 550. https://doi.org/10.1186/s13059-014-0550-8
5. Ewels, P., et al. (2016). MultiQC: summarize analysis results for multiple tools and samples in a single report. *Bioinformatics*, 32(19), 3047–3048. https://doi.org/10.1093/bioinformatics/btw354
6. Brooks, A. N., et al. (2011). Conservation of an RNA regulatory map between Drosophila and mammals. *Genome Research*, 21(2), 193–202. https://doi.org/10.1101/gr.108662.110

---

*This repository was prepared as part of a Bioinformatics course assignment at NUST.*
*All analyses were performed on Galaxy Europe using publicly available datasets.*
