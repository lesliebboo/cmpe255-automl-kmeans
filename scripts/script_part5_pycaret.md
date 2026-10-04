# Video Script: Part 5 - PyCaret: Capabilities Tour
**Author:** Weihao Fu

---

Hi, I'm Weihao Fu. This video tours PyCaret, the low-code machine learning library.

**[0:00 - 1:00] What is PyCaret?**

PyCaret wraps multiple ML libraries (scikit-learn, LightGBM, XGBoost) in a simple workflow:
```python
exp = setup(data, target="label")
best_model = compare_models()
```

It handles preprocessing, model comparison, tuning, and interpretation in just a few lines.

**[1:00 - 3:00] Setup and Data Prep**

The `setup()` function is where the magic happens. It:
- Infers data types
- Handles missing values
- Encodes categoricals
- Splits train/test
- Sets up cross-validation

I demonstrate on a telecom churn dataset with 3000 customers.

**[3:00 - 5:00] Model Comparison**

`compare_models()` trains and cross-validates dozens of algorithms, then ranks them by your chosen metric. We sort by AUC and see LightGBM, Random Forest, and Gradient Boosting at the top.

PyCaret automatically logs everything to MLflow for experiment tracking.

**[5:00 - 7:00] Model Interpretation**

Two key tools:

1. `interpret_model()` with SHAP: shows which features drive predictions for individual customers. The beeswarm plot reveals that tenure and contract type are most important.

2. Permutation importance: measures the drop in performance when each feature is shuffled. This tells us what the deployed model relies on.

**[7:00 - 8:30] Fairness and Imbalance**

I demonstrate:
- `fix_imbalance`: SMOTE oversampling for the minority class
- Fairness metrics: compare performance across customer segments

**[8:30 - 9:30] Takeaways**

PyCaret's strengths:
- Minimal code for full ML workflow
- Built-in experiment tracking
- Easy model interpretation
- Good for rapid prototyping

The tradeoff: less control than writing sklearn code directly, but much faster to iterate.

Thanks for watching!
