# Video Script: Part 2 - AutoGluon: Capabilities Tour
**Author:** Weihao Fu

---

Hi, I'm Weihao Fu. This video tours AutoGluon's capabilities across different problem types.

**[0:00 - 1:00] What is AutoGluon?**

AutoGluon is Amazon's AutoML library. You give it data and a label column; it handles feature engineering, model selection, hyperparameter tuning, and ensembling automatically.

The key API is simple:
```python
predictor = TabularPredictor(label="target").fit(train_data)
predictions = predictor.predict(test_data)
```

**[1:00 - 3:00] Tabular: Binary Classification**

First, telecom churn prediction. I generate synthetic customer data with a planted churn mechanism. AutoGluon trains multiple models - LightGBM, Random Forest, Extra Trees - and ensembles them.

We evaluate with ROC-AUC. Notice how AutoGluon automatically handles categorical features and missing values.

**[3:00 - 4:30] Tabular: Multiclass & Regression**

Next, loan grade prediction (multiclass) and house price regression. Same API, different problem types. AutoGluon detects the problem type from the label column.

For regression, we use mean absolute error as the metric.

**[4:30 - 6:00] Time Series Forecasting**

AutoGluon also does time series with `TimeSeriesPredictor`. I demonstrate on synthetic demand data with multiple time series. We specify:
- `prediction_length`: how far to forecast
- `target`: the column to predict
- `quantile_levels`: for probabilistic forecasts

**[6:00 - 7:30] Multimodal: Text + Tabular**

For the review helpfulness task, we have tabular features PLUS free text. AutoGluon's `MultiModalPredictor` handles this by fine-tuning a transformer on the text while jointly training on tabular features.

**[7:00 - 8:30] Model Zoo Comparison**

Finally, I compare the full model zoo against TabM (a tabular foundation model) and a fine-tuned foundation model. We look at the tradeoff between accuracy and inference time.

**[8:30 - 9:00] Takeaways**

AutoGluon's strengths:
- One API for many problem types
- Automatic feature engineering and ensembling
- Competitive performance with minimal code
- Handles text, images, and time series

Thanks for watching!
