# Video Script: Part 3 - AutoGluon: End-to-End
**Author:** Weihao Fu

---

Hi, I'm Weihao Fu. This video shows a complete end-to-end machine learning workflow using AutoGluon.

**[0:00 - 1:30] Problem Setup**

We're predicting customer churn for a telecom company. The workflow covers:
1. Data preparation and feature engineering
2. Model training with AutoGluon
3. Model calibration
4. Hyperparameter optimization
5. Deployment considerations

**[1:30 - 3:30] Data Preparation**

I start with raw customer data: demographics, service usage, billing info. Key steps:
- Create a `fit_tabular` helper that standardizes our training calls
- Set a fixed CPU budget for reproducibility
- Split into train/validation/test

**[3:30 - 5:30] Baseline Training**

We train AutoGluon with different evaluation metrics (F1, ROC-AUC, Log Loss) to see how the metric choice affects model selection. AutoGluon automatically tries multiple algorithms and creates a weighted ensemble.

**[5:30 - 7:00] Model Calibration**

Raw predicted probabilities are often miscalibrated. I demonstrate temperature scaling: learn a single parameter T on validation data that softens or sharpens the probabilities to minimize log loss.

We measure calibration with Expected Calibration Error (ECE).

**[7:00 - 8:30] Hyperparameter Optimization**

For LightGBM, I run random search over:
- `num_leaves`: tree complexity
- `learning_rate`: step size
- `feature_fraction`: column sampling

We do 5 trials and compare validation vs test performance to check for overfitting.

**[8:30 - 9:30] Feature Importance & Conclusion**

Finally, we look at permutation importance to understand which features drive predictions. Tenure and monthly charges are typically the top predictors for churn.

Key lessons:
- AutoGluon handles the heavy lifting, but you still need to understand your data
- Calibration matters for probability outputs
- HPO gives modest gains; good features matter more

Thanks for watching!
