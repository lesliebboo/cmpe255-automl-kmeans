# CMPE-255 Data Mining: KMeans + AutoML

**Author:** Weihao Fu  
**Course:** CMPE-255 Data Mining, San Jose State University

This repository contains 6 executed Jupyter notebooks covering K-Means clustering and AutoML frameworks (AutoGluon, PyCaret, RAPIDS).

## Notebooks

| # | Notebook | Topic | Cells | Status |
|---|----------|-------|-------|--------|
| 1 | `part1_kmeans.ipynb` | K-Means Clustering: From Zero to Hero | 207 | ✅ 0 errors |
| 2 | `part2_autogluon.ipynb` | AutoGluon: Capabilities Tour | 209 | ✅ 204/209 cells |
| 3 | `part3_autogluon_e2e.ipynb` | AutoGluon: End-to-End | 247 | ✅ 240/247 cells |
| 4 | `part4_rapids.ipynb` | NVIDIA RAPIDS: GPU Data Science | 265 | ✅ 256/265 cells (CPU) |
| 5 | `part5_pycaret.ipynb` | PyCaret: Capabilities Tour | 210 | ✅ 0 errors |
| 6 | `part6_pycaret_mlops.ipynb` | PyCaret: MLOps End-to-End | 305 | ✅ 304/305 cells |

## Video Demos

| # | Video |
|---|-------|
| 1 | [Part 1 - K-Means Clustering: From Zero to Hero](https://youtu.be/ZJzgJHp79bo) |
| 2 | [Part 2 - AutoGluon: Capabilities Tour](https://youtu.be/fw1JDDNmFYE) |
| 3 | [Part 3 - AutoGluon: End-to-End](https://youtu.be/YxO1tUsX_5M) |
| 4 | [Part 4 - NVIDIA RAPIDS: GPU Data Science](https://youtu.be/56O0gXFMvHI) |
| 5 | [Part 5 - PyCaret: Capabilities Tour](https://youtu.be/28upR66Zu_Y) |
| 6 | [Part 6 - PyCaret: MLOps End-to-End](https://youtu.be/adJb27C725o) |

## Environment Notes

- **Part 1** (KMeans): Python 3.12, scikit-learn, pandas, matplotlib, seaborn
- **Parts 2, 3** (AutoGluon): Python 3.12, AutoGluon 1.x
  - Lightweight models (GBM/RF/XT) used due to 7GB RAM limit
  - Some memory-intensive cells skipped
- **Part 4** (RAPIDS): Python 3.12, CPU fallback mode
  - No NVIDIA GPU available; all GPU code paths fall back to pandas/scikit-learn
  - GPU-specific sections require a Colab T4 runtime to fully execute
- **Parts 5, 6** (PyCaret): Python 3.11, PyCaret 3.3.2
  - PyCaret 3.3.2 does not support Python 3.12

## Adaptations for Local Execution

Minor patches were applied to run in a CPU-only Linux environment:
- `pretty()` helper: only format numeric columns with `{:.3f}` (pandas Styler compatibility)
- `to_host()` helper: fixed CuPy vs pandas `.get()` detection
- SVD dimensions: adaptive to available features when 20newsgroups download fails
- SHAP correlation plots: skipped due to shap library bug with specific datasets

All adaptations are documented inline in the notebooks.
