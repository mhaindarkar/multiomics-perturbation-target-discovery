# 🧬 Multi-Omics Perturbation Target Discovery

A reproducible bioinformatics pipeline to identify therapeutic targets by **reversing disease-associated pathway signatures** and validating them using **single-cell transcriptomics** and **multi-omics evidence**.

---

## 🚀 Project Overview

Understanding disease mechanisms at the pathway level enables systematic identification of therapeutic interventions.

This project implements an end-to-end pipeline:

* Derives **disease pathway signatures** from bulk RNA-seq
* Compares them against **perturbation-induced pathway signatures**
* Identifies **reversal candidates using anticorrelation analysis**
* Validates findings using **real single-cell RNA-seq data (Scanpy)**
* Integrates evidence into a **final ranked list of therapeutic candidates**

---

## 🧠 Core Idea

A good therapeutic candidate should:

* Reverse disease-associated pathways
* Show consistent effects across datasets
* Be supported by cellular-level expression evidence

This is achieved using:

```
Disease → Pathways → Perturbation → Anticorrelation → Validation → Ranking
```

---

## 📊 Pipeline Overview

```
Bulk RNA-seq (GSE235236)
        ↓
Differential Expression (DEG)
        ↓
GSEA (MSigDB Hallmark)
        ↓
Disease Pathway Signature
        ↓
Perturbation Signatures (LINCS-style curated)
        ↓
Perturbation GSEA
        ↓
Disease vs Perturbation Anticorrelation
        ↓
Single-cell Validation (Scanpy, GSE214695)
        ↓
Multi-omics Integration
        ↓
Final Therapeutic Ranking
```

---

## 📁 Repository Structure

```
multiomics-perturbation-target-discovery/
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── notebooks/
├── results/
│   ├── tables/
│   └── figures/
├── src/
├── scripts/
├── docs/
├── environment.yml
└── README.md
```

---

## 🔬 Data Sources

### Bulk RNA-seq (Disease Signature)

* Dataset: **GSE235236**
* Groups:

  * UC (Ulcerative Colitis)
  * CD (Crohn’s Disease)
  * HC (Healthy Control)

### Single-cell RNA-seq (Validation)

* Dataset: **GSE214695**
* Tissue: Colonic mucosa
* Used for:

  * Cell-type-specific expression
  * Target validation

### Perturbation Data

* Curated LINCS-style signatures
* Drugs:

  * Dexamethasone
  * Budesonide
  * Tofacitinib
  * Ruxolitinib

---

## ⚙️ Methods

### 1. Differential Expression

* Log2FC + Welch t-test
* Multiple testing correction (FDR)

### 2. Pathway Enrichment

* Method: GSEA / FGSEA
* Database: MSigDB Hallmark 2020

### 3. Anticorrelation Analysis

* Pearson & Spearman correlation
* Negative correlation = pathway reversal

### 4. Single-Cell Validation

* Tool: Scanpy
* Steps:

  * QC filtering
  * Normalization
  * PCA / UMAP / Leiden clustering
  * Cell-type annotation
  * Target expression & DE analysis

### 5. Multi-Omics Integration

* Combines:

  * Pathway reversal score
  * Single-cell support
  * (Optional) proteomics evidence

---

## 📈 Key Results

### 🧪 Top Perturbations

Identified candidates show strong reversal of disease pathways and biological relevance:

* Glucocorticoids (e.g., dexamethasone, budesonide)
* JAK inhibitors (e.g., tofacitinib, ruxolitinib)

These are consistent with known therapies for inflammatory bowel disease.

---

## 📊 Key Figures

### 🔝 Final Integrated Ranking

![Ranking](results/figures/integration_final_perturbation_ranking_barplot.png)

### 🧠 Multi-Omics Evidence Integration

![Heatmap](results/figures/integration_evidence_component_heatmap.png)

### 🧬 Single-Cell Validation (UMAP)

![UMAP](results/figures/sc_real_umap_celltypes.png)

### 🎯 Target Expression Across Cell Types

![Dotplot](results/figures/sc_real_target_expression_dotplot.png)

---

## 🧬 Biological Interpretation

* Disease signatures show strong enrichment of:

  * Inflammatory pathways
  * Cytokine signaling
  * Interferon responses

* Top perturbations reverse these pathways:

  * Glucocorticoids → suppress inflammation
  * JAK inhibitors → block cytokine signaling

* Single-cell data confirms:

  * Targets are expressed in relevant cell types
  * Differential regulation across UC vs HC

---

## ⚠️ Limitations

* Single-cell analysis uses a reduced subset (2 HC + 2 UC for efficiency)
* Proteomics layer is framework-ready but not populated with real data
* Cell-type annotation is simplified

---

## 🧩 Future Work

* Integrate real proteomics datasets
* Add drug perturbation signatures (beyond curated lists)
* Use pseudobulk DE for single-cell analysis
* Expand to additional diseases

---

## 🛠️ How to Run

### 1. Create environment

```bash
conda env create -f environment.yml
conda activate multiomics
```

### 2. Run notebooks in order

```
01_data_processing.ipynb
02_disease_gsea.ipynb
03_perturbation_gsea.ipynb
04_anticorrelation.ipynb
05_single_cell_scanpy_real_minimal_2HC_2UC_corrected.ipynb
05_single_cell_fixed.ipynb
06_proteomics_fixed.ipynb
07_integration.ipynb
08_final_summary_report.ipynb
```

---

## 💡 Key Highlights

* End-to-end **multi-omics pipeline**
* Combines **bulk + perturbation + single-cell**
* Uses **pathway-level reasoning (not just genes)**
* Produces **interpretable drug rankings**
* Fully **reproducible and modular**

---

## 👤 Author

Vaibhav Mhaindarkar
PhD in Biotechnology | Protein Biochemistry & Bioinformatics

---

## ⭐ Summary

This project demonstrates how to:

* Translate transcriptomics into actionable insights
* Identify therapeutic candidates using pathway reversal
* Validate findings at the cellular level
* Build reproducible pipelines for translational research

---
