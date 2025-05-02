# RNA-Seq Profiling of Human Urinary-Derived Renal Epithelial Cells for Therapeutic Insights in NPHP1-Associated Nephronophthisis

This repository contains a series of R scripts used for the analysis of RNA sequencing (RNA-seq) data from patient-derived human urine-derived renal epithelial cells (hURECs). The study focuses on understanding the molecular mechanisms and potential therapeutic strategies for Nephronophthisis (NPHP), an autosomal recessive kidney disorder caused by mutations in the NPHP1 gene.

## Project Overview

Nephronophthisis (NPHP) is a leading genetic cause of kidney failure in children and young adults. The NPHP1 gene encodes nephrocystin-1, a protein that plays key roles in the primary cilium and cellular junctions. This project aims to explore the molecular pathways involved in NPHP1 deletion by analyzing RNA-seq data from hURECs derived from a family with a homozygous NPHP1 gene deletion. The project also explores therapeutic interventions, specifically testing a prostaglandin E2 receptor agonist and and EGFR kinase inhibitor, with the aim to restore the disease-associated transcriptomic profile and ameliorate the phenotypic manifestations observed in patient-derived hURECs.


![image](https://github.com/user-attachments/assets/b8183225-f608-4db0-9a2a-30bf8b7d9b5b)

## Script Descriptions

### Step 1: Gene-level Count Matrix Generation
**Script:** `summarize_gene_counts.R`
- **Description:** Generates a gene-level count matrix from RNA-seq BAM files.
- **Inputs:** BAM files of RNA-seq samples.
- **Outputs:** Gene count matrix in a tabular format.

### Step 2: RNA-seq Preprocessing and PCA Plotting
**Script:** `RNA_Seq_Preprocessing.R`
- **Description:** Performs preprocessing of RNA-seq data, including filtering and normalization. It also plots a Principal Component Analysis (PCA) to visualize sample variability.
- **Inputs:** Raw count matrix generated from Step 1.
- **Outputs:** PCA plot and normalized data for downstream analysis.

### Step 3: Cell-Type Marker Expression in hURECs
**Script:** `CellType_markers_QC.R`
- **Description:** Analyzes the expression of specific cell-type gene markers in the hUREC samples to assess the purity and identity of the cell population.
- **Inputs:** Normalized RNA-seq data and cell-type gene markers.
- **Outputs:** Visualizations of gene expression for selected cell-type markers.

### Step 4: Differential Expression Analysis using DESeq2
**Script:** `4_Differential_Expression_Analysis.R`
- **Description:** Performs differential expression analysis using DESeq2 to identify genes that are differentially expressed between various conditions 
- **Inputs:** Normalized RNA-seq data.
- **Outputs:** Differentially expressed gene (DEG) results including p-values, fold changes, and gene annotations.

### Step 5: Volcano Plot of DEGs
**Script:** `Volcano_plot.R`
- **Description:** Plots a volcano plot to visualize differentially expressed genes (DEGs) based on p-value and log2 fold change.
- **Inputs:** DEG results from Step 4.
- **Outputs:** Volcano plot visualization highlighting DEGs.

### Step 6: Pathway Enrichment Analysis
**Script:** `Pathway_Enrichment_Analysis.R`
- **Description:** Performs pathway enrichment analysis using Gene Set Enrichment Analysis (GSEA) or MetaScape, and visualizes the results with network plots, clusters, or bar plots.
- **Inputs:** DEG results from Step 4 and Metascape results.
- **Outputs:** Visualizations of enriched pathways (e.g., bar plots, network plots).

### Step 7: Comparing DEG Sets Across Treatments
**Script:** `comparin_DEG_sets.R`
- **Description:** Compares lists of differentially expressed genes (DEGs) from different differential expression analyses. This script loads DESeq2 results for various treatments, filters them based on significance (p-value < 0.05 and log2 fold change > 0.58), and compares the lists of DEGs between disease signatures and treatments.
- **Inputs:** DESeq2 results for different treatments (e.g., Case-Control, AG556, ALP).
- **Outputs:** Comparison results between disease signatures and treatments, including interesting (opposite direction) genes.

## Prerequisites

Before running these scripts, ensure that you have the following dependencies installed in your R environment:

- `dplyr`
- `DESeq2`
- `ggplot2`
- `pheatmap`
- `clusterProfiler`
- `enrichplot`

To install these packages, you can run the following commands:

```R
install.packages("dplyr")
install.packages("ggplot2")
install.packages("pheatmap")
BiocManager::install("DESeq2")
BiocManager::install("clusterProfiler")
BiocManager::install("enrichplot")
