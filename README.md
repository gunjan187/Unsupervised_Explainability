# Unsupervised Explainability: Dimensionality Reduction & Model-Agnostic Methods

## Overview

This project provides a framework to apply **SHAP** and **LIME** to **unsupervised models** using **dimensionality reduction (DR)** methods like **PCA**, **t-SNE**, and **UMAP**. The goal is to make unsupervised models more interpretable and reveal how original features influence reduced components.

## Datasets Used

- **Data.csv**: Baseline dataset with high-dimensional features.
- **log_tpm.csv**: RNA expression data.
- **tissue_gene_expression.csv**: Gene expression data across tissues.
- **Colorectal Cancer Data.csv**: Gene expression for colorectal cancer.

## Installation

Clone the repo and install dependencies:

```bash
git clone https://github.com/gunjan187/Unsupervised_Explainability.git
cd Unsupervised_Explainability
pip install -r requirements.txt
```

## Example Usage

1. Load your data (e.g., `Data.csv`) and apply **PCA**, **t-SNE**, or **UMAP** for dimensionality reduction.
2. Use **SHAP** for global feature importance and **LIME** for local instance explanations.

```python
# Example of PCA for dimensionality reduction
from sklearn.decomposition import PCA

pca = PCA(n_components=2)
X_pca = pca.fit_transform(X_scaled)

# Apply SHAP to explain PCA components
import shap
explainer = shap.Explainer(model, X_scaled)
shap_values = explainer(X_scaled)
shap.plots.beeswarm(shap_values)
```

### Visualizing t-SNE

```python
from sklearn.manifold import TSNE
import matplotlib.pyplot as plt

tsne = TSNE(n_components=2, perplexity=30)
X_tsne = tsne.fit_transform(X_scaled)
plt.scatter(X_tsne[:, 0], X_tsne[:, 1], c='blue')
plt.title('t-SNE Visualization')
plt.show()
```

## Contributing

Feel free to fork and submit pull requests for improvements.
