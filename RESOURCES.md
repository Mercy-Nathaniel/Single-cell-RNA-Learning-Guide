# Single-cell RNA-seq Learning Resources

## Essential Documentation

### Scanpy
- **Official Documentation:** https://scanpy.readthedocs.io/
- **GitHub:** https://github.com/theislab/scanpy
- **Paper:** Wolf et al. (2018) - Genome Biology

### AnnData
- **Documentation:** https://anndata.readthedocs.io/
- **GitHub:** https://github.com/scverse/anndata
- **Object format:** `.h5ad` files

### Seurat (for comparison)
- **Documentation:** https://satijalab.org/seurat/
- **Vignettes:** https://satijalab.org/seurat/archive/v4/articles/

---

## Key Publications & Review Articles

### Essential Reading

1. **Luecken & Theis (2019)** - "Best practices in single-cell RNA-seq analysis: a tutorial"
   - Current opinion in Systems Biology
   - Gold standard workflow overview
   - **Read this first before coding**

2. **Heumos et al. (2023)** - "Best practices for single-cell analysis across modalities"
   - Nature Reviews Methods Primers
   - Modern comprehensive review
   - Covers integration and batch effects

3. **Bizzotto et al. (2021)** - "Approaches to preprocessing single-cell RNA-seq data"
   - Current Protocols
   - Practical troubleshooting guide

### Background on scRNA-seq

- Tang et al. (2009) - "mRNA-Seq whole-transcriptome analysis of a single cell" - Science
- Picelli et al. (2013) - "Smart-seq2 for sensitive full-length transcriptome profiling in single cells"
- Zheng et al. (2017) - "Massively parallel digital transcriptional profiling of single cells"

---

## Online Tutorials & Courses

### Video Tutorials
- **Scanpy tutorials:** https://www.youtube.com/results?search_query=scanpy+tutorial
- **Orchestrating Single-cell Analysis with Bioconductor:** https://bioconductor.org/books/release/OSCA/

### Interactive Courses
- **SingleCellMentorship:** Free online course on scRNA-seq
- **CZI Data Science:** https://data.humancellatlas.org/analyze

### GitHub Repositories with Tutorials
- https://github.com/theislab/scanpy_tutorials
- https://github.com/satijalab/seurat

---

## Public Datasets for Practice

### Built into Scanpy
```python
import scanpy as sc

# PBMC 3K - what we'll use for learning
adata = sc.datasets.pbmc3k()

# Other built-in datasets
adata = sc.datasets.pbmc10k()
adata = sc.datasets.pbmc68k()
adata = sc.datasets.visium_sge()
```

### Public Data Repositories

**Gene Expression Omnibus (GEO)**
- https://www.ncbi.nlm.nih.gov/geo/
- Search for "scRNA-seq" or specific cell types
- Download from: Series → Supplementary Files

**Human Cell Atlas**
- https://www.humancellatlas.org/
- Standardized, quality-controlled datasets
- Multiple tissue types and organisms

**10x Genomics Sample Data**
- https://www.10xgenomics.com/resources/datasets
- Official tutorial datasets
- Various sequencing platforms

**Zenodo/Figshare**
- Academic repositories with published datasets
- Search for specific diseases or tissues

---

## Tools & Complementary Software

### For Batch Effect Correction
- **Harmony** - Fast, multi-omic compatible
- **Combat** - From bulk RNA-seq but adapted for scRNA
- **scVI** - Deep learning approach

### For Trajectory Inference
- **CellRank** - Probabilistic framework
- **Monocle 3** - Pseudotime ordering
- **RNA Velocity (Velocyto)** - Directional information

### For Spatial Transcriptomics
- **Squidpy** - Spatial analysis with Scanpy integration
- **Giotto** - R/Python framework
- **SpatialDE** - Spatial pattern detection

### For Multimodal Data
- **muon** - Multi-omics analysis (pairs with Scanpy)
- **MOFA+** - Factor analysis
- **Seurat v5** - Multimodal integration

---

## Community Resources

### Forums & Discussion
- **Scanpy GitHub Issues:** https://github.com/theislab/scanpy/issues
- **Biostars:** https://www.biostars.org/ (tag: scRNA-seq)
- **Stack Overflow:** Search [scanpy] or [seurat]

### Twitter/X Communities
- Follow: @theislab, @satijalab
- Hashtags: #singlecellRNA #scRNAseq #bioinformatics

### Conferences & Workshops
- **Genomics Standards Consortium** - scRNA-seq workshops
- **Cold Spring Harbor Laboratory** - Advanced sequencing courses
- **COMBINE** - Bioinformatics education

---

## Cheat Sheets

### Quick Scanpy Syntax
```python
# QC
sc.pp.calculate_qc_metrics(adata)
sc.pp.filter_cells(adata, min_genes=200)
sc.pp.filter_genes(adata, min_cells=3)

# Preprocessing
sc.pp.normalize_total(adata)
sc.pp.log1p(adata)
sc.pp.highly_variable_genes(adata)

# Dimensionality reduction
sc.tl.pca(adata)
sc.pp.neighbors(adata)
sc.tl.umap(adata)
sc.tl.tsne(adata)

# Clustering & annotation
sc.tl.leiden(adata)
sc.tl.rank_genes_groups(adata)

# Plotting
sc.pl.umap(adata, color='cell_type')
sc.pl.dotplot(adata, var_names, groupby='cell_type')
sc.pl.violin(adata, var_names, groupby='cell_type')
```

---

## Recommended Reading Order

1. **Week 1:** Read Luecken & Theis (2019) + this RESOURCES.md
2. **Week 2:** Bizzotto et al. (2021) + Scanpy docs on preprocessing
3. **Week 3:** OSCA chapter on dimensionality reduction
4. **Week 4:** OSCA chapter on clustering
5. **Week 5:** Heumos et al. (2023) for comprehensive perspective

---

## Tips for Learning

✅ **Do:**
- Read background first, then code
- Run tutorials on provided datasets before your own data
- Take notes on why each step matters
- Join online communities and ask questions
- Revisit papers as you understand more

❌ **Don't:**
- Skip normalization steps "just to see"
- Use random clustering parameters without justification
- Trust automated annotations without validation
- Assume one tool is universally better than another

---

## Getting Help

When stuck:
1. Check Scanpy documentation and examples
2. Search GitHub issues for similar problems
3. Read related papers for context
4. Ask on Biostars with reproducible example
5. Contact Scanpy developers (GitHub issues)

Happy learning! 🧬
