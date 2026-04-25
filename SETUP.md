# Environment Setup for Single-cell RNA-seq Learning

## Why Setup Matters

Proper environment setup ensures:
- Reproducibility across machines
- Correct package versions that don't conflict
- Easy collaboration with others
- Clean separation from system Python

---

## Prerequisites

You need:
- Python 3.9+ (check with `python --version`)
- Conda or pip installed
- ~5GB of disk space for packages and sample data

---

## Option 1: Using Conda (Recommended)

### Step 1: Create Conda environment

```bash
conda create -n scrna-learning python=3.10 -y
conda activate scrna-learning
```

### Step 2: Install Scanpy and dependencies

```bash
conda install -c conda-forge scanpy anndata -y
```

### Step 3: Install Jupyter and visualization tools

```bash
conda install -c conda-forge jupyter matplotlib seaborn pandas numpy scikit-learn scipy -y
```

### Step 4: Verify installation

```python
import scanpy as sc
import anndata as ad
print(f"Scanpy version: {sc.__version__}")
print(f"AnnData version: {ad.__version__}")
```

---

## Option 2: Using pip (if Conda unavailable)

### Step 1: Create virtual environment

```bash
python -m venv scrna-learning
source scrna-learning/bin/activate  # On Windows: scrna-learning\Scripts\activate
```

### Step 2: Upgrade pip

```bash
pip install --upgrade pip
```

### Step 3: Install from requirements.txt

```bash
pip install -r requirements.txt
```

### Step 4: Verify installation

```python
import scanpy as sc
import anndata as ad
print(f"Scanpy version: {sc.__version__}")
print(f"AnnData version: {ad.__version__}")
```

---

## Running Jupyter Notebooks

### Start Jupyter

```bash
jupyter notebook
```

OR (newer interface)

```bash
jupyter lab
```

Your browser will open automatically with the notebook interface.

---

## Setting Up R/Seurat (Optional, for comparison)

For Seurat comparison notebooks:

```bash
# Install R first, then in R console:
install.packages("Seurat")
install.packages("SeuratData")
```

OR install rpy2 to call R from Python:

```bash
conda install -c conda-forge rpy2
# OR
pip install rpy2
```

---

## Downloading Sample Data

### PBMC 3K Dataset (used in tutorials)

Scanpy downloads automatically on first use:

```python
import scanpy as sc
adata = sc.datasets.pbmc3k()
```

OR manually:

```bash
mkdir data
cd data
wget https://www.dropbox.com/s/33ui2lh0p0ue6ea/pbmc3k_raw.h5ad?dl=1
```

---

## Troubleshooting

### Issue: "ModuleNotFoundError: No module named 'scanpy'"

**Solution:** Ensure your environment is activated

```bash
conda activate scrna-learning
# OR
source scrna-learning/bin/activate
```

### Issue: "ImportError: cannot import name '_version' from 'scanpy'"

**Solution:** Update Scanpy

```bash
conda update scanpy -y
# OR
pip install --upgrade scanpy
```

### Issue: Slow Scanpy import

**Solution:** This is normal on first import (~5-10 seconds). Subsequent imports are faster.

---

## Next Steps

1. Navigate to `notebooks/` folder
2. Open `00_introduction.ipynb`
3. Follow `LEARNING_PROGRESS.md` for week-by-week guidance

Happy learning! 🧬
