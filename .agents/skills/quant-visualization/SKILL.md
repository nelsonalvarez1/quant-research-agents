---
name: quant-visualization
description: Create transparent diagnostic charts for trading experiments and validation reports.
---

# Quant visualisation

Use Matplotlib for diagnostic figures; prepare series with pandas or NumPy as required. Declare dependencies with `uv add`; run with `uv run --locked`. Save plotted values, axis conventions and figure configuration.

Plot equity curves with split boundaries and benchmarks, drawdowns, rolling volatility and rolling Sharpe when sample length permits. Show applicable turnover, exposure, parameter sensitivity and regime results. Label units, frequency, costs, dates and sample size. Distinguish gross and net results. Avoid axes or smoothing that conceal losses. Mark unavailable or undefined metrics; do not fabricate curves.
