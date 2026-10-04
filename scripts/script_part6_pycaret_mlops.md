# Video Script: Part 6 - PyCaret: MLOps End-to-End
**Author:** Weihao Fu

---

Hi, I'm Weihao Fu. This video shows a complete MLOps workflow using PyCaret, from training to deployment to monitoring.

**[0:00 - 1:30] The MLOps Lifecycle**

We'll cover:
1. Train and select the best model
2. Finalize and save the model
3. Deploy as a REST API
4. Monitor for drift
5. Retrain when needed

**[1:30 - 3:30] Training and Selection**

Starting with the churn dataset, I use PyCaret to compare models and select the best LightGBM classifier. Key steps:
- `setup()` with proper validation strategy
- `compare_models()` sorted by AUC
- `tune_model()` for hyperparameter optimization

**[3:30 - 5:00] Model Finalization**

`finalize_model()` retrains on the full dataset (train + validation). Then `save_model()` persists the entire pipeline - preprocessing AND model - to a pickle file.

This is crucial: the saved object includes all the transformations, so deployment sees the same features.

**[5:00 - 7:00] Deployment as API**

PyCaret can generate a FastAPI app from the saved model. The API has:
- `/predict`: single prediction endpoint
- Automatic input validation with Pydantic
- Swagger docs at `/docs`

I demonstrate with test customer data.

**[7:00 - 8:30] Monitoring for Drift**

In production, data changes. I demonstrate:
- Population Stability Index (PSI): measures distribution shift
- Performance monitoring: track AUC over time
- When PSI > 0.25 or AUC drops, trigger retraining

**[8:30 - 9:30] Takeaways**

PyCaret MLOps gives you:
- One-line model deployment
- Built-in monitoring hooks
- Easy retraining workflow

For production at scale you'd use Kubeflow or SageMaker, but PyCaret is perfect for getting from notebook to API quickly.

Thanks for watching!
