# 5-Week Single-cell RNA-seq Learning Plan

## Overview

This is your structured learning roadmap for May 1-31, 2026.
Each week builds on the previous. Follow sequentially.

**Start date:** May 1, 2026  
**End date:** May 31, 2026

---

## Week 1: Foundations (May 1-7)
### Concepts: Understanding scRNA-seq from the ground up

**Learning Outcomes:**
- Understand what scRNA-seq measures and why it's useful
- Learn about AnnData object structure
- Load and explore a basic single-cell dataset
- Create first visualizations

**Tasks:**
- [ ] Complete `SETUP.md` - install all packages
- [ ] Read `notebooks/00_introduction.ipynb` - what is scRNA-seq?
- [ ] Read `notebooks/01_anndata_structure.ipynb` - understanding AnnData
- [ ] Load PBMC dataset and explore dimensions
- [ ] Create first UMAP (don't worry if it looks weird yet)

**Key Concepts:**
- Cell × Gene expression matrix
- `.X` (matrix), `.obs` (observations/metadata), `.var` (variables/genes)
- Counts vs normalized data

**Practice:**
```python
import scanpy as sc
adata = sc.datasets.pbmc3k()  # Load tutorial dataset
print(adata)  # Explore structure
print(adata.obs)  # Cell metadata
print(adata.var)  # Gene information
```

**Deliverable:** Completed notebook with AnnData exploration

---

## Week 2: Data Processing (May 8-14)
### Quality Control & Normalization

**Learning Outcomes:**
- Perform quality control on raw counts
- Normalize and log-transform data
- Identify and remove low-quality cells
- Understand why each step matters

**Tasks:**
- [ ] Read `notebooks/02_quality_control.ipynb`
- [ ] Calculate QC metrics (n_genes, n_counts, mt%)
- [ ] Plot QC metrics and set filtering thresholds
- [ ] Filter cells and genes
- [ ] Normalize with `sc.pp.normalize_total()`
- [ ] Log transform with `sc.pp.log1p()`

**Key Concepts:**
- Mitochondrial gene percentage (cell viability indicator)
- Minimum/maximum gene counts per cell
- Library size normalization
- Why log-transformation?

**Practice:**
```python
# QC metrics
adata.var['mt'] = adata.var_names.str.startswith('MT-')
sc.pp.calculate_qc_metrics(adata, qc_vars=['mt'], inplace=True)

# Filtering
sc.pp.filter_cells(adata, min_genes=200)
sc.pp.filter_genes(adata, min_cells=3)

# Normalization
sc.pp.normalize_total(adata, target_sum=1e4)
sc.pp.log1p(adata)
```

**Deliverable:** Processed dataset with QC plots saved

---

## Week 3: Dimensionality Reduction (May 15-21)
### PCA, UMAP, and Visualizing High-dimensional Data

**Learning Outcomes:**
- Understand PCA and why it's important
- Learn neighbor-finding algorithms
- Create UMAP embeddings
- Interpret and troubleshoot visualizations

**Tasks:**
- [ ] Read `notebooks/03_dimensionality_reduction.ipynb`
- [ ] Perform HVG (highly variable genes) selection
- [ ] Run PCA and plot scree plot
- [ ] Compute neighborhood graph (k-nearest neighbors)
- [ ] Generate UMAP embedding
- [ ] Create high-quality UMAP plots

**Key Concepts:**
- Curse of dimensionality
- Why PCA before UMAP?
- UMAP parameters: `n_neighbors`, `min_dist`
- Interpreting 2D projections (they're not perfect!)

**Practice:**
```python
# HVGs
sc.pp.highly_variable_genes(adata, n_top_genes=2000)

# PCA
sc.tl.pca(adata, n_comps=50)
sc.pl.pca_variance_ratio(adata, log=True)

# UMAP
sc.pp.neighbors(adata, n_neighbors=15, n_pcs=50)
sc.tl.umap(adata)
sc.pl.umap(adata, color=['n_genes', 'n_counts'])
```

**Deliverable:** UMAP visualization + PCA scree plot

---

## Week 4: Cell Type Identification (May 22-28)
### Clustering & Annotation

**Learning Outcomes:**
- Cluster cells into groups
- Find marker genes for each cluster
- Annotate clusters with cell types
- Interpret biological meaning

**Tasks:**
- [ ] Read `notebooks/04_clustering_annotation.ipynb`
- [ ] Leiden clustering at multiple resolutions
- [ ] Find marker genes with `sc.tl.rank_genes_groups()`
- [ ] Visualize markers on UMAP
- [ ] Create dotplot and violin plots
- [ ] Annotate clusters manually (use reference if available)

**Key Concepts:**
- What is Leiden algorithm?
- Resolution parameter (affects cluster number)
- Marker genes = cluster identity
- Differential expression basics

**Practice:**
```python
# Clustering
sc.tl.leiden(adata, resolution=0.5)

# Find markers
sc.tl.rank_genes_groups(adata, 'leiden', method='wilcoxon')

# Visualize
sc.pl.umap(adata, color='leiden')
sc.pl.rank_genes_groups_dotplot(adata)

# Manual annotation
adata.obs['cell_type'] = adata.obs['leiden'].map({
    '0': 'CD4 T cells',
    '1': 'CD8 T cells',
    '2': 'B cells',
    # ... etc
})
```

**Deliverable:** Annotated cell types + marker gene heatmap

---

## Week 5: Advanced Topics & Synthesis (May 29-31)
### Scanpy vs Seurat Comparison & Publication-ready Figures

**Learning Outcomes:**
- Understand Seurat workflow equivalents
- Create publication-quality figures
- Troubleshoot and validate results
- Plan next research steps

**Tasks:**
- [ ] Read `notebooks/05_scanpy_vs_seurat.ipynb` (Scanpy version)
- [ ] Compare workflow side-by-side (concepts same, syntax different)
- [ ] Create final publication figures (UMAPs, violins, dotplots)
- [ ] Write summary analysis of PBMC dataset
- [ ] Plan how to apply to your own data
- [ ] Create `ANALYSIS_SUMMARY.md` documenting findings

**Key Concepts:**
- Both tools answer same questions, different approaches
- Publication standards for scRNA-seq figures
- Batch effects and integration (preview)

**Practice:**
```python
# Publication-quality UMAP
sc.pl.umap(
    adata,
    color='cell_type',
    legend_loc='on data',
    frameon=False,
    size=100,
    palette='tab20'
)

# Combined dotplot
markers = ['CD4', 'CD8A', 'MS4A1', 'CD14', 'CD68']
sc.pl.dotplot(adata, markers, groupby='cell_type', cmap='viridis')
```

**Deliverable:** Comparison notebook + final analysis summary

---

## Progress Tracker

Update this as you progress:

```
✅ = Completed
🔄 = In Progress
⬜ = Not started

Week 1 (Foundations): ⬜
  - Setup: ⬜
  - Introduction: ⬜
  - AnnData: ⬜
  - First visualization: ⬜

Week 2 (Processing): ⬜
  - QC metrics: ⬜
  - Filtering: ⬜
  - Normalization: ⬜
  - Log transform: ⬜

Week 3 (Reduction): ⬜
  - HVG selection: ⬜
  - PCA: ⬜
  - Neighbors: ⬜
  - UMAP: ⬜

Week 4 (Annotation): ⬜
  - Clustering: ⬜
  - Markers: ⬜
  - Visualization: ⬜
  - Manual annotation: ⬜

Week 5 (Advanced): ⬜
  - Scanpy vs Seurat: ⬜
  - Publication figures: ⬜
  - Summary analysis: ⬜
```

---

## Success Criteria by End of May 31

✅ All 5 notebooks completed  
✅ PBMC dataset fully analyzed and annotated  
✅ Understanding of Scanpy workflow  
✅ Comfortable with AnnData objects  
✅ Ready to apply to own single-cell data  
✅ Basic knowledge of Seurat for comparison  

---

## Beyond Week 5

Next steps for June onwards:
- Apply workflow to your own datasets
- Learn batch effect correction
- Explore trajectory inference
- Connect to your spatial transcriptomics research
- Review recent scRNA-seq publications

You've got this! 🧬📊
