# Immune Cell Profiling Using Flow Cytometry and Dimensionality Reduction

Automated immune cell profiling from flow cytometry data using PCA and t-SNE, with clinical implications for COVID-19 immune monitoring and diagnostic panel optimisation.

## Background

During the COVID-19 pandemic, rapid immune profiling was critical for predicting disease severity and guiding treatment. Traditional flow cytometry analysis relies on manual gating — a slow, subjective process that doesn't scale well during a health crisis. This project demonstrates that unsupervised dimensionality reduction can automatically identify and separate immune cell populations, offering a faster, more reproducible alternative.

## What This Project Does

- Analyses flow cytometry data from a healthy control sample (1,000 cells, 21 surface markers) published in a longitudinal COVID-19 immune profiling study (Lucas et al., *Science Immunology*, 2020)
- Applies **PCA** to identify the markers most responsible for separating immune cell types and determine the minimum number of dimensions needed to represent the data
- Applies **t-SNE** across six perplexity values (5, 10, 15, 30, 50, 80) to find the optimal non-linear embedding for visualising all eight cell populations
- Identifies key clinical markers: **CD3** for T cell separation, **HLA-DR** and **CD14** for monocyte isolation, **SSC-A/H** and **CD10** for neutrophil detection

## Key Findings

| Finding | Detail |
|---------|--------|
| Variance captured | 8 PCs explain 82.50% of total variance |
| PC1 drivers | SSC-A (0.337), SSC-H (0.335), CD10 (0.298) — separates neutrophils from lymphocytes |
| PC2 drivers | HLA-DR (0.544), CD14 (0.407) — isolates monocytes |
| Best t-SNE | Perplexity 50 — cleanest separation of all 8 cell types |
| Minimal panel | 4 markers (SSC-A, CD3, CD14, HLA-DR) capture the majority of clinically relevant variation |

## Clinical Relevance

- **COVID-19 triage**: Low CD3+ T cell counts predict severe disease and ICU admission. Automated detection of T cell depletion could serve as an early warning system.
- **Monocyte monitoring**: Reduced HLA-DR on monocytes indicates immune paralysis and poor prognosis. PCA-based tracking could supplement clinical judgement in the ICU.
- **Panel optimisation**: A reduced 4-marker panel could make immune profiling accessible in resource-limited hospitals and low-income healthcare settings.
- **Beyond COVID-19**: The pipeline generalises to bone marrow transplant monitoring, leukaemia minimal residual disease detection, immunotherapy response evaluation, and primary immunodeficiency screening.

## Cell Types Identified

| Cell Type | Count | Percentage |
|-----------|-------|------------|
| Neutrophils | 427 | 42.7% |
| T cells | 342 | 34.2% |
| Monocytes | 85 | 8.5% |
| NK cells | 56 | 5.6% |
| Eosinophils | 38 | 3.8% |
| Basophils | 30 | 3.0% |
| B cells | 16 | 1.6% |
| DC cells | 6 | 0.6% |

## Tech Stack

- **Python** (NumPy, Pandas, Scikit-learn, Matplotlib, Plotly)
- **PCA** — linear dimensionality reduction and marker importance analysis
- **t-SNE** — non-linear embedding for cluster visualisation
- **StandardScaler** — z-score normalisation for equal feature weighting

## Project Structure

```
├── flow cytometry (covid-19).ipynb   # Main analysis notebook
├── FlowData1000.csv                  # Dataset (1,000 cells x 21 markers)
├── Flow_Cytometry_Immune_Profiling_Report.pdf  # Full academic report
└── README.md
```

## Data Source

Lucas, C., Wong, P., Klein, J., et al. (2020). *Longitudinal analyses reveal immunological misfiring in severe COVID-19.* Nature, 584(7821), 463–469. [https://www.science.org/doi/full/10.1126/sciimmunol.abd6197](https://www.science.org/doi/full/10.1126/sciimmunol.abd6197)

## Author

**Judah Akinlajar** — Data Scientist
