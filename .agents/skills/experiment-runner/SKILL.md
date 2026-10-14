---
name: experiment-runner
description: Make systematic trading experiments reproducible and comparable through configs and result metadata.
---

# Experiment runner

Restore Python 3.12 with `uv sync --locked`; run experiments with `uv run --locked`. Add packages with `uv add`; commit `pyproject.toml` and `uv.lock` together. Record Python and direct dependency versions for each completed experiment.

Save configuration for data version, split boundaries, hypothesis and baseline IDs, parameters, execution, costs, slippage and applicable random seeds. Record code version, timestamp, status and metric conventions. Write artefacts to `results/<run_id>/`; log every trial in `research/experiments.csv`, including failures and missing-value reasons. Compare runs on identical samples and metric definitions. Keep synthetic fixtures separate from empirical evidence. Freeze the final test split before viewing results.
