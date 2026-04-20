# Multi-Omics Perturbation Target Discovery

A reproducible pipeline to identify therapeutic perturbations and candidate targets by reversing disease-associated pathway signatures and validating them using multi-omics evidence.

---

## Project Overview

Many diseases are driven by coordinated pathway dysregulation rather than changes in single genes alone.

This project identifies therapeutic opportunities by integrating:

* disease transcriptomics
* pathway-level signatures (GSEA)
* perturbation response data
* single-cell RNA-seq validation
* proteomics evidence

---

## Core Idea

Disease → DEG → GSEA
Perturbation → GSEA → Anticorrelation
Single-cell → Cell-type context
Proteomics → Validation
Integration → Final prioritization

A strong candidate should:

* reverse disease pathways
* be biologically relevant
* be supported across multiple omics layers

---

## Dataset

### Disease dataset

* GSE235236
* Bulk transcriptomics
* Main contrast: UC vs HC

### Single-cell dataset

* GSE214695
* Used with Scanpy
* Subsampled (2 HC + 2 UC) for reproducibility

### Perturbations (curated)

* Dexamethasone
* Budesonide
* Tofacitinib
* Ruxolitinib

---

## Key Results

### Top perturbations (final integrated ranking)

| Rank | Perturbation  | Mechanism      | Final Integrated Score |
| ---- | ------------- | -------------- | ---------------------- |
| 1    | Tofacitinib   | JAK inhibitor  | ~1.00                  |
| 2    | Ruxolitinib   | JAK inhibitor  | ~0.80                  |
| 3    | Dexamethasone | Glucocorticoid | ~0.51                  |
| 4    | Budesonide    | Glucocorticoid | ~0.40                  |

These results are biologically consistent with:

* suppression of inflammatory cytokine signaling
* inhibition of JAK–STAT pathways
* activation of glucocorticoid response programs

---

### Top supported targets

| Gene    | Evidence                                |
| ------- | --------------------------------------- |
| TSC22D3 | Strong glucocorticoid response signal   |
| FKBP5   | Steroid-responsive regulator            |
| JAK1    | Central inflammatory signaling mediator |
| TYK2    | Cytokine signaling pathway component    |

Supported by:

* pathway dysregulation
* perturbation reversal
* single-cell expression
* partial proteomics validation

---

## Pipeline Overview

1. QC and DEG generation
2. Disease pathway enrichment (GSEA)
3. Perturbation pathway profiling
4. Anticorrelation analysis
5. Single-cell validation
6. Proteomics validation
7. Multi-omics integration
8. Final summary reporting

---

## Repository Structure

```
multiomics-perturbation-target-discovery/
├── notebooks/
│   ├── 00_project_walkthrough.ipynb
│   ├── 01_qc_and_deg_final.ipynb
│   ├── 02_disease_gsea.ipynb
│   ├── 02.01_build_ranked_perturbation_signatures_helper.ipynb
│   ├── 03_perturbation_gsea_lincs.ipynb
│   ├── 04_anticorrelation.ipynb
│   ├── 05_single_cell_scanpy_real_minimal_2HC_2UC_corrected.ipynb
│   ├── 05_single_cell.ipynb
│   ├── 06_proteomics.ipynb
│   ├── 07_integration.ipynb
│   ├── 08_final_summary_report.ipynb
│
├── data/
│   ├── raw/                # not tracked (GEO data)
│   ├── processed/
│
├── results/
│   ├── tables/
│   ├── figures/
│
├── src/
├── scripts/
├── docs/
├── README.md
├── environment.yml
└── requirements.txt
```

---

## Main Outputs

### Tables

* final_anticorrelation_ranking.tsv
* final_single_cell_target_validation.tsv
* final_proteomics_target_validation.tsv
* final_integrated_perturbation_ranking.tsv
* final_integrated_target_ranking.tsv
* final_summary_report_bundle.xlsx

### Figures

* perturbation ranking plots
* integration heatmaps
* single-cell UMAP / dotplots
* final summary visualizations

---

## Proteomics Validation (Current Status)

Proteomics is included as a validation layer, but:

* uses partial/example datasets
* not all targets have protein evidence
* acts as **supporting validation, not primary driver**

### Interpretation

Final ranking is mainly driven by:

1. pathway anticorrelation
2. single-cell validation

Proteomics contributes:

* additional confidence where available

---

## Reproducibility

This repository is fully reproducible.

⚠️ Note:

* raw data is not included (GEO download required)
* large files and caches are excluded
* small subsets are used for local execution

---

## Final Biological Question

Which therapeutic perturbations and target genes are most strongly supported by:

* disease transcriptomics
* pathway dysregulation
* perturbation reversal
* cell-type specificity
* protein-level evidence

---

## Summary

This project demonstrates an end-to-end workflow for:

* disease signature analysis
* perturbation-based target discovery
* multi-omics integration
* biologically interpretable prioritization

---

## Author

Vaibhav Mhaindarkar
PhD Biotechnology
Protein Biochemistry → Bioinformatics Transition
