---
name: strategy-validation
description: Independently validate a trading result for out-of-sample robustness, costs, and leakage.
---

# Strategy validation

Use SciPy, statsmodels or scikit-learn where required. Declare dependencies with `uv add`; run with `uv run --locked`. Keep estimator and cross-validation splits chronological.

Fit preprocessing and tune parameters on permitted earlier data only. Preserve explicit training, validation and final test boundaries; never optimise on the final holdout. Use walk-forward evaluation when sample length permits. Check neighbouring parameters, costs, slippage, regimes, sample size and uncertainty. Audit feature availability, labels, universe membership, revisions and split boundaries for leakage. Compare with the prespecified baseline and report failures. Reach validation conclusions independently of strategy development.
