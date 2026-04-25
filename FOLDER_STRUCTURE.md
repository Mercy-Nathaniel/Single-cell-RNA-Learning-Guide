# Single-cell RNA-seq Learning Repository Structure

## Why Structure Matters

Good organization helps you:
- Find code quickly
- Avoid duplicate work
- Share reproducibly with others
- Scale to multiple projects

---

## Recommended Folder Layout

```
Single-cell-RNA-Learning-Guide/
│
├── README.md                      # Overview (already exists)
├── SETUP.md                       # Installation & environment
├── LEARNING_PROGRESS.md           # 5-week plan (this file)
├── RESOURCES.md                   # Links & references
├── FOLDER_STRUCTURE.md            # This file
│
├── requirements.txt               # Python dependencies
├── .gitignore                     # What to exclude from Git
│
├── notebooks/                     # Jupyter notebooks (main learning)
│   ├── 00_introduction.ipynb
│   ├── 01_anndata_structure.ipynb
│   ├── 02_quality_control.ipynb
│   ├── 03_dimensionality_reduction.ipynb
│   ├── 04_clustering_annotation.ipynb
│   ├── 05_scanpy_vs_seurat.ipynb
│   └── README.md                  # Notebook guide
│
├── concepts/                      # Deep-dive concept explanations
│   ├── qc_metrics_explained.md
│   ├── pca_vs_umap.md
│   ├── why_log_transform.md
│   ├── clustering_resolution.md
│   └── README.md
│
├── practical_examples/            # Standalone example scripts
│   ├── load_10x_data.py
│   ├── batch_correction_example.py
│   ├── celltype_annotation.py
│   └── README.md
│
├── cheatsheets/                   # Quick reference
│   ├── scanpy_commands.md
│   ├── common_errors.md
│   ├── parameter_guide.md
│   └── README.md
│
├── data/                          # Sample datasets (git-ignored)
│   ├── pbmc3k/
│   └── .gitkeep
│
├── results/                       # Output from analyses (git-ignored)
│   ├── figures/
│   ├── tables/
│   └── .gitkeep
│
└── images/                        # Screenshots & diagrams
    ├── workflow_diagram.png
    └── README.md
```

---

## Folder Descriptions

### `notebooks/`

**Purpose:** Main learning materials - step-by-step Jupyter notebooks

**Files:**
- `00_introduction.ipynb` - What is scRNA-seq? Why do we do it?
- `01_anndata_structure.ipynb` - Understanding the AnnData object
- `02_quality_control.ipynb` - QC metrics, filtering, normalization
- `03_dimensionality_reduction.ipynb` - PCA, neighbors, UMAP
- `04_clustering_annotation.ipynb` - Leiden, markers, cell types
- `05_scanpy_vs_seurat.ipynb` - Comparison with R Seurat

**How to use:**
- Start with 00, go sequentially
- Follow along line-by-line
- Modify code to understand what each line does
- Save your outputs to `results/`

### `concepts/`

**Purpose:** Deeper explanations of why things work

**Files:**
- `qc_metrics_explained.md` - Why we filter cells/genes
- `pca_vs_umap.md` - Mathematical intuition
- `why_log_transform.md` - Statistical justification
- `clustering_resolution.md` - Parameter tuning guide

**How to use:**
- Read alongside relevant notebook
- Review when you don't understand a step
- Reference when writing your own analyses

### `practical_examples/`

**Purpose:** Standalone Python scripts for common tasks

**Files:**
- `load_10x_data.py` - Load real 10x Genomics data
- `batch_correction_example.py` - Harmonizing multiple batches
- `celltype_annotation.py` - Automated annotation

**How to use:**
```bash
python practical_examples/load_10x_data.py
```

Copy and adapt for your own datasets.

### `cheatsheets/`

**Purpose:** Quick lookup reference

**Files:**
- `scanpy_commands.md` - One-liner Scanpy functions
- `common_errors.md` - Troubleshooting guide
- `parameter_guide.md` - What do all these parameters do?

**How to use:**
- Bookmark for quick lookup
- Search when you forget syntax
- Reference when learning parameter choices

### `data/`

**Purpose:** Local storage for sample datasets

**Note:** This folder is `.gitignore`'d (files don't upload to GitHub)

**Files:**
- `pbmc3k/` - PBMC 3K tutorial dataset
- Other datasets you download for practice

**Size warning:** Single-cell datasets can be large!
- Scanpy auto-downloads to this folder
- Keep your `.gitignore` updated to avoid accidentally committing

### `results/`

**Purpose:** Outputs from your analyses

**Structure:**
```
results/
├── figures/          # PNG, PDF plots
├── tables/           # CSV, TSV results
└── processed_data/   # .h5ad intermediate files
```

**Note:** Also `.gitignore`'d - commit code, not large output files

---

## Getting Started

### Step 1: Clone or create local copy

```bash
git clone https://github.com/Mercy-Nathaniel/Single-cell-RNA-Learning-Guide.git
cd Single-cell-RNA-Learning-Guide
```

### Step 2: Set up environment

```bash
conda create -n scrna-learning python=3.10 -y
conda activate scrna-learning
pip install -r requirements.txt
```

### Step 3: Create data and results folders

```bash
mkdir -p data results/figures results/tables
```

### Step 4: Start learning

```bash
jupyter notebook notebooks/
```

Open `00_introduction.ipynb` and begin!

---

## Adding Your Own Content

As you learn, add files:

### Custom notebooks

Place in `notebooks/`:
```
notebooks/06_my_custom_analysis.ipynb
```

### Custom analysis scripts

Place in `practical_examples/`:
```
practical_examples/my_disease_analysis.py
```

### Learning notes

Place in `concepts/`:
```
concepts/notes_on_batch_effects.md
```

---

## Committing to GitHub

Keep repository clean with proper `.gitignore`:

```bash
# Track code
git add notebooks/*.ipynb
git add practical_examples/*.py
git add *.md

# Don't track large files
git add .gitignore

# Commit
git commit -m "Add clustering notebook and updated progress"
git push
```

---

## Memory Considerations

Keep your local system fast:

| File Type | Size | Commit? |
|-----------|------|----------|
| `.ipynb` notebooks | 1-10 MB | ✅ Yes |
| `.py` scripts | <1 MB | ✅ Yes |
| `.h5ad` data | 100 MB - 1 GB | ❌ No |
| PNG figures | 1-5 MB | ⚠️ Selectively |
| CSV results | 1-50 MB | ⚠️ Selectively |

---

## Tips for Organization

✅ **Do:**
- Name notebooks sequentially (00_, 01_, ...)
- Use descriptive folder names
- Keep `.gitignore` up to date
- One analysis per notebook
- Add comments explaining goals

❌ **Don't:**
- Commit raw data to GitHub
- Use vague names like "test.ipynb"
- Store analysis steps in 20 different notebooks
- Forget to document what outputs mean
- Leave notebooks unsaved with transient notes

---

## Next: Start with SETUP.md

You're ready! Follow:
1. `SETUP.md` - Install packages
2. `LEARNING_PROGRESS.md` - Follow 5-week plan
3. `notebooks/00_introduction.ipynb` - Begin learning

Happy organizing! 🧬📁
