# Architecture and research governance

## What this repository provides

This repository is an instruction and workflow framework. `AGENTS.md` provides shared governance; the 12 skill files give focused guidance for recurring research tasks. It does not implement data acquisition, signals, a backtester, or analysis software. Paths such as `src/backtest.py` and `research/experiments.csv` in `AGENTS.md` are a suggested structure for a separate experiment workspace, not files shipped here.

## Governance

The governing requirements are in `AGENTS.md`:

- Challenge assumptions, use parsimonious methods, and distinguish evidence from conjecture.
- Commit the economic hypothesis and evaluation specification before backtesting. Define when inputs become available and when trades can execute.
- Record every variant and failure in a trial ledger.
- Freeze the final holdout specification before access and never tune on holdout results.
- Report net transaction costs, benchmarks, uncertainty, sensitivity, risk, liquidity, and capacity.
- Check material claims against primary sources and make the code and paper reproduce the same results.
- Track configuration and dependencies, separate acquisition from evaluation, and prevent implicit downloads, retuning, or holdout access.
- Preserve data manifests with availability timestamps, adjustments, and hashes. Keep credentials outside source control and confirm data entitlements and cost before acquisition.

For submission papers, `AGENTS.md` specifies a five-page limit including figures and tables, at least 11-point type, standard margins, and references and an optional appendix excluded from the limit. Check current official submission rules before applying those constraints to a particular event.

## Skill responsibilities

| Research stage | Skills | Main responsibility |
| --- | --- | --- |
| Frame the question | `quant-research`, `alpha-research` | State a mechanism, falsifiable prediction, baseline, and a limited candidate set. |
| Establish data validity | `financial-data`, `market-data-integration` | Validate schema, provenance, timestamps, provider semantics, and cleaning; isolate vendor access. |
| Build causal inputs | `financial-time-series` | Specify shifts, endpoints, warm-up, preprocessing, and leakage checks. |
| Implement evaluation | `quant-backtesting`, `experiment-runner` | Define executable timing and accounting; preserve configurations, run metadata, and all trials. |
| Select and challenge | `strategy-optimization`, `strategy-validation` | Bound search to permitted samples; check out-of-sample behavior, costs, sensitivity, and leakage independently. |
| Explain evidence | `portfolio-risk`, `quant-visualization`, `quant-reporting` | State metric conventions, show transparent diagnostics, and report results and limitations supported by recorded evidence. |

Skills are task guidance, not executable components or proof that a requested analysis has been performed.

## Preregistration and trial control

Before a backtest, record the hypothesis, null or baseline, data and universe, availability and decision times, execution model, holding period, portfolio rules, costs, metrics, sample boundaries, and planned comparisons. Set any optimization ranges, objective, budget, and seeds in advance. Keep a chronological trial ledger that includes unsuccessful runs and missing-value reasons. Compare runs only on compatible samples and metric definitions.

The suggested workspace layout in `AGENTS.md` stores the specification in `research/hypothesis.md`, the trial ledger in `research/experiments.csv`, and run configurations, data hashes, trades, returns, and metrics under `results/<run_id>/`. A new research workspace should create those files only after their behavior and schema are defined.

## Data, features, and backtesting

Validate raw data before feature engineering. Record source, units, instrument identifiers, timezone, exchange calendar, interval meaning, value availability, revisions, corporate actions, and universe changes. Preserve raw inputs. Document resampling, return conventions, and every imputation or exclusion.

Build features only from observations available at decision time. Define shifts, window endpoints, warm-up periods, missing-value rules, and preprocessing explicitly. Fit normalisation and model parameters on training data only. Check labels, revisions, centered windows, global statistics, and universe membership for future information leakage.

In backtests, distinguish signals, executed positions, turnover, gross PnL, costs, and net PnL. A signal made after an interval cannot earn that interval's return. Use fills supported by the data and market mechanics. State cost units and applicable cash, leverage, financing, corporate-action, and rebalancing rules. Test timing and accounting with synthetic hand-computable cases before empirical evaluation.

## Validation and holdout safeguards

Use chronological training, validation, and final test samples. Fit preprocessing and tune parameters only on permitted earlier data. Use walk-forward evaluation when the sample permits. Compare against the prespecified baseline, inspect neighboring parameter settings, and examine sensitivity to costs, slippage, regimes, sample size, and uncertainty. Keep all attempted configurations and failures.

Freeze the final test definition and evaluation choices before viewing its results. Do not optimize on the final holdout. Report holdout access in the trial record. Audit availability times, labels, revisions, universe membership, and split boundaries for leakage. Synthetic fixtures are software checks, not empirical performance evidence.

## Metrics, reporting, and reproducibility

State return type and frequency, annualization factor, risk-free rate, downside target, volatility convention, fee inclusion, drawdown start, turnover convention, and hit-rate unit. Distinguish undefined metrics from zero and report sample counts. Present net results with benchmarks, costs, uncertainty, risk, liquidity, capacity, sensitivities, and failed robustness checks.

Record code version, data version and hashes, runtime and direct dependency versions, configuration, timestamp, status, seeds where applicable, and metric conventions. Preserve plotted values and figure settings. The final report must match the recorded run configuration and be reproducible from code; unsupported performance claims must not be added.
