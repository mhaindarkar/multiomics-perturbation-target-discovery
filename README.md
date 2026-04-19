# multiomics-perturbation-target-discovery

A reproducible multi-omics pipeline that identifies therapeutic targets by reversing disease-associated pathway signatures and validating them using single-cell and proteomics data.

---

## Motivation

Many diseases are driven by dysregulated biological pathways rather than individual genes. 
This project aims to identify therapeutic targets by integrating multiple layers of biological evidence.

---

## Core Idea

Disease → DEG → GSEA  
Perturbation → GSEA → Anticorrelation  
Single-cell → Cell-type origin  
Proteomics → Validation  
→ Integration → Final target prioritization  

---

## Pipeline Overview

1. Transcriptomics (RNA-seq / microarray)
2. Differential expression
3. Pathway enrichment (GSEA)
4. Perturbation pathway comparison
5. Anticorrelation analysis
6. Single-cell validation
7. Proteomics validation
8. Integration and target prioritization

---

## Repository Structure

- notebooks/ → step-by-step analysis
- src/ → reusable functions
- data/ → raw and processed data
- results/ → tables and figures
- scripts/ → pipeline execution
- docs/ → diagrams

---

## Current Status

- [x] Project setup
- [ ] Bulk transcriptomics QC and DEG
- [ ] Disease GSEA
- [ ] Perturbation analysis
- [ ] Anticorrelation ranking
- [ ] Single-cell validation
- [ ] Proteomics validation
- [ ] Integration
- [ ] Final target prioritization

---

## How to Run

```bash
conda env create -f environment.yml
conda activate multiomics

python scripts/run_pipeline.py