---
name: financial-time-series
description: Construct and inspect causal financial time-series features and statistical diagnostics.
---

# Financial time series

Use pandas and NumPy for indexed operations; add SciPy or statsmodels when diagnostics require them. Declare dependencies with `uv add`; run with `uv run --locked`.

Build lagged features and rolling statistics from observations available at decision time. Specify shifts, window endpoints, warm-up periods, missing values and resampling rules. Fit normalisation and model parameters on training data only. Assess autocorrelation, nonstationarity, structural breaks and regression assumptions. Check shifted labels, centred windows, revisions and global statistics for future-information leakage. Verify non-obvious transformations with synthetic alignment tests.
