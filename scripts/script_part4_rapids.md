# Video Script: Part 4 - NVIDIA RAPIDS: GPU Data Science
**Author:** Weihao Fu

---

Hi, I'm Weihao Fu. This video explores NVIDIA RAPIDS for GPU-accelerated data science.

**[0:00 - 1:30] What is RAPIDS?**

RAPIDS is a suite of GPU-accelerated libraries that mirror the PyData ecosystem:
- cuDF: GPU DataFrames (like pandas)
- cuML: GPU ML algorithms (like scikit-learn)
- cuGraph: GPU graph analytics (like NetworkX)
- CuPy: GPU arrays (like NumPy)

The key idea: same API as CPU libraries, but runs on GPU.

**[1:30 - 3:00] The GPU Contract**

This notebook is designed to run on both GPU and CPU. We detect GPU availability with `nvidia-smi`, then set:
- `xdf = cudf if GPU else pd` (DataFrame library)
- `xp = cupy if GPU else numpy` (array library)

Helper functions like `to_host()` convert GPU objects back to CPU for plotting.

**[3:00 - 5:00] Data Manipulation with cuDF**

I demonstrate cuDF on a household budget dataset:
- Filtering, groupby, aggregations - same syntax as pandas
- The performance difference is striking on large data

On CPU, this falls back to pandas automatically.

**[5:00 - 7:00] Machine Learning with cuML**

For ML, cuML provides GPU versions of:
- LogisticRegression
- RandomForestClassifier
- KMeans

I train a churn classifier and compare GPU vs CPU timing. The `cuml.accel` profiler shows which sklearn calls can be accelerated.

**[7:00 - 8:30] XGBoost on GPU**

XGBoost has native GPU support via `tree_method="hist"` and `device="cuda"`. I show the speedup on a 50K row dataset.

Note: This requires an XGBoost build with CUDA support.

**[8:30 - 9:30] When to Use RAPIDS**

RAPIDS shines when:
- Data fits in GPU memory (typically 8-24GB)
- Operations are vectorized (not Python loops)
- You're doing many iterations (ML training)

For small data, CPU pandas is often faster due to GPU transfer overhead.

Thanks for watching!
