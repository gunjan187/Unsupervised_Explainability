# X-DRXAI: Explainable Dimensionality-Reduction-Driven Unsupervised Learning

**X-DRXAI** is a novel machine learning pipeline designed to bring explainability to unsupervised learning tasks by combining dimensionality reduction, clustering, and post hoc explanation techniques. It is especially effective for analyzing high-dimensional datasets such as gene expression profiles.

---

## Overview

Unsupervised models like KMeans or DBSCAN often fail to explain why certain clusters are formed, particularly in biological datasets. This project introduces a model-agnostic pipeline where:

- **PCA** is used to preserve linear variance,
- **UMAP** enhances non-linear separability,
- **KMeans** clusters the reduced data,
- **SHAP** and **LIME** generate explanations per cluster,
- **A feedback loop** refines features based on SHAP values to improve clustering coherence and interpretability.

---

## Project Structure

```
Unsupervised_explainability/
│
├── X_DRXAI_Colorectal Cancer Gene Expression Data.ipynb
├── X_DRXAI_Data.ipynb
├── X_DRXAI_log_tpm.ipynb
├── X_DRXAI_tissue_gene_expression.ipynb
│
├── New_Datasets/
│   ├── Colorectal Cancer Gene Expression Data.csv
│   ├── Data.csv
│   ├── log_tpm.csv
│   └── tissue_gene_expression.csv
```

Each notebook runs the complete X-DRXAI pipeline on a different biological dataset.

---

## Key Features

### Preprocessing
- Handles missing values
- One-hot encoding for categorical variables
- Feature standardization using `StandardScaler`

### Dimensionality Reduction
- **PCA** (n=10) to reduce initial dimensions
- **UMAP** (n=2) for final 2D embedding
- Explained variance plots and 95% cutoff threshold visualized

### Clustering
- **KMeans** with default 3 clusters (can be tuned)
- **Silhouette Score** calculated for performance
- Cluster visualizations with Seaborn

### 🔎 Explainability
- **SHAP** applied using one-vs-all logistic regression classifiers
- Global feature importance shown as SHAP bar plots
- **LIME** used to locally explain specific instances

### Feedback Loop
- Features with SHAP values above a threshold are retained
- The model is optionally re-run on refined data
- A new silhouette score and cluster plot are generated

---

## Outputs

Each notebook produces:
- PCA explained variance and cumulative plots
- UMAP visualizations of clusters
- SHAP summary bar plots per cluster
- Optional LIME explanations per sample
- A refined dataset based on SHAP feature thresholds
- Feature count barplots post-refinement

---

## Datasets Used

All datasets are sourced from open biological repositories and contain high-dimensional gene expression or tissue-specific data:

- `Colorectal Cancer Gene Expression Data.csv`
- `log_tpm.csv` – Log-transformed transcripts per million
- `tissue_gene_expression.csv`
- `Data.csv` – Additional gene dataset from repository

> Source: https://github.com/jeremy-goldwasser/feature-rankings

---

## Installation (Optional for Reproduction)

This project uses Python 3.8+  
To run the notebooks:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn umap-learn shap lime
```

You may also want to install `jupyterlab` or run on Google Colab for GPU-accelerated SHAP explanations.

---

## Goals

- Improve model transparency in high-dimensional unsupervised tasks
- Identify and visualize which features drive each cluster
- Provide researchers with interpretable groupings in omics datasets

---

## Citation

If using this work for academic or research purposes, please cite:

> Sharma, G. (2025). *X-DRXAI: Explainable Dimensionality-Reduction-Driven Unsupervised Learning*. Deakin University.

---

## Author

**Gunjan Sharma**  
Bachelor of Software Engineering (Honours),  
Deakin University, Australia  
[LinkedIn](https://www.linkedin.com) (optional)
