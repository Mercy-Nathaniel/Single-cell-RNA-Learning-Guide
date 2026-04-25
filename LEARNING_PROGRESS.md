# Learning Progress Tracker

Track my learning journey through scRNA-seq analysis. I'll update this as I complete concepts and exercises.

**Timeline: April 25 - May 31, 2026 (5 weeks)**

---

## Week 1 (Apr 25-May 1): Foundations

### Concepts to Learn
- [ ] What is single-cell RNA-seq (scRNA-seq)?
- [ ] Data structures: UMI, gene expression matrices, AnnData objects
- [ ] Quality control metrics (nGenes, nCounts, % mitochondrial)
- [ ] Why normalization matters
- [ ] Difference between Scanpy and Seurat workflows

### Little Bets
- [ ] Set up environment (conda, packages installed)
- [ ] Load first scRNA-seq dataset (PBMC 3K or similar)
- [ ] Explore AnnData structure
- [ ] Create first QC plots

### Resources to Review
- [ ] Scanpy tutorial: https://scanpy.readthedocs.io/
- [ ] 10x Genomics: What is scRNA-seq?
- [ ] AnnData documentation

**Status:** ⏳ Not started

---

## Week 2 (May 2-8): Data Processing

### Concepts to Learn
- [ ] Quality control filtering (low-quality cells, doublets)
- [ ] Normalization methods (library size, log transformation)
- [ ] Batch effect detection
- [ ] Gene selection and HVGs (highly variable genes)

### Little Bets
- [ ] Implement QC filtering pipeline
- [ ] Compare normalized vs unnormalized distributions
- [ ] Select HVGs and understand why
- [ ] Visualize batch effects (if applicable)

### Resources to Review
- [ ] Luecken & Theis (2019) - Best practices paper
- [ ] Scanpy preprocessing functions

**Status:** ⏳ Not started

---

## Week 3 (May 9-15): Dimensionality Reduction & Clustering

### Concepts to Learn
- [ ] Why dimensionality reduction is needed
- [ ] PCA: principal component analysis
- [ ] t-SNE vs UMAP: differences and when to use
- [ ] K-means clustering (basic concept)
- [ ] Leiden/Louvain clustering algorithms

### Little Bets
- [ ] Run PCA on your dataset
- [ ] Generate UMAP and t-SNE plots
- [ ] Compare results and understand differences
- [ ] Perform Leiden clustering
- [ ] Visualize clusters on reduction plots

### Resources to Review
- [ ] UMAP paper: McInnes et al. (2018)
- [ ] Scanpy tutorial on clustering
- [ ] Comparison: t-SNE vs UMAP

**Status:** ⏳ Not started

---

## Week 4 (May 16-22): Cell Type Identification & Annotation

### Concepts to Learn
- [ ] Differential gene expression analysis
- [ ] Marker genes and how to find them
- [ ] Manual vs automated cell type annotation
- [ ] Gene set enrichment analysis (GSEA)
- [ ] Comparing with reference datasets

### Little Bets
- [ ] Find marker genes for each cluster
- [ ] Visualize top markers
- [ ] Annotate clusters manually using markers
- [ ] Learn GSEA basics (optional: implement)

### Resources to Review
- [ ] Scanpy: Finding marker genes
- [ ] CellMarker database
- [ ] Seurat integration for comparison

**Status:** ⏳ Not started

---

## Week 5 (May 23-31): Advanced Topics & Seurat Comparison

### Concepts to Learn
- [ ] Trajectory inference (pseudotime analysis)
- [ ] RNA velocity basics
- [ ] Integration of multiple datasets
- [ ] Key differences: Scanpy vs Seurat implementation
- [ ] Spatial transcriptomics concepts (bridge to your visual cortex work)

### Little Bets
- [ ] Implement same workflow in Seurat (conceptually)
- [ ] Document key differences between tools
- [ ] Explore one advanced topic (trajectory or RNA velocity)
- [ ] Create final comparison notebook
- [ ] Document lessons learned

### Resources to Review
- [ ] Seurat tutorial: https://satijalab.org/seurat/
- [ ] RNA velocity: https://velocyto.org/
- [ ] Spatial transcriptomics overview

**Status:** ⏳ Not started

---

## Confusing Topics & Solutions

Tracking things that confused me for reference:

| Topic | What Confused Me | Solution/Clarification |
|-------|-----------------|----------------------|
| AnnData structure | | |
| Normalization methods | | |
| Clustering parameters | | |
| Marker gene interpretation | | |

---

## Completed Resources

- [ ] Tutorial: (title)
- [ ] Paper: (citation)
- [ ] Practice exercise: (description)

