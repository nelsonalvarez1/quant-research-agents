# Example: a hypothetical daily reversal study

This is a proposed research plan, not a report of completed work. The signal, data, split dates, costs, thresholds, and expected outcome below are illustrative choices. No backtest has been run and no performance result is claimed.

## Question and hypothesis

Study whether unusually weak recent returns among liquid equities predict a partial reversal over the next trading session. A possible mechanism is temporary price pressure, but the study must test that explanation rather than assume it. The null is that the candidate does not outperform a prespecified no-signal baseline after costs.

## Preregistered evaluation plan

Before accessing backtest outcomes, write the final specification to `research/hypothesis.md` and record a run identifier and specification version. The plan should settle:

- **Universe:** A point-in-time list of liquid equities, including delisted names where data permits. Define liquidity eligibility using only information available before each decision.
- **Input and timing:** Daily adjusted and raw price fields with source, adjustment policy, timezone, exchange calendar, and availability documented. Calculate a five-session return through the close of session *t*. Generate the signal after that close and submit orders for execution at the next session's open. Do not credit the signal with any return ending before its decision time.
- **Signal and portfolio:** Rank eligible securities by the preceding five-session return. The initial candidate buys the bottom decile, with equal weights, and exits at the following close. It is a long-only portfolio. The decile, weighting, and holding rule are fixed before evaluation.
- **Baseline:** Compare against cash and a prespecified equal-weight long-only universe portfolio on identical dates.
- **Costs and constraints:** Specify commissions, spread, slippage, fill assumptions, position limits, and capacity diagnostics. Do not substitute zero for unavailable cost observations.
- **Metrics:** Prespecify net cumulative and annualized return, volatility, Sharpe, maximum drawdown, turnover, exposure, trade counts, and a measure of uncertainty. State each metric's frequency, annualization, fee treatment, and denominator conventions.
- **Splits:** Use chronological training, validation, and final test periods. Select actual dates only after inspecting data coverage and before looking at outcomes. Freeze the final test period and access procedure in the specification.
- **Comparisons:** Limit exploration to the baseline and the one candidate above. If a later variant is justified, record the reason and update the trial ledger before running it; do not present a post hoc variant as prespecified.

## Data checks before features

Use `financial-data` to inventory files, fields, units, provenance, identifiers, ordering, missingness, duplicates, outliers, corporate actions, delistings, and universe changes. Confirm that the daily close and next open are available at the stated decision and execution times. Preserve raw inputs and record the reproducible cleaning rules and hashes.

Use `financial-time-series` to verify that the five-session return uses only sessions through *t*, with the correct window endpoints. Check warm-up rows, adjustment revisions, point-in-time membership, and all forward-fills or exclusions. Use synthetic alignment cases to test the feature and label timestamps.

## Implementation and experiments

Create the signal, execution, and accounting code only after the behavior is specified. Use `quant-backtesting` to keep signals, target weights, fills, executed positions, turnover, gross return, costs, and net return separate. Test next-open entry and next-close exit with a hand-calculable fixture that includes missing opens and a trading halt.

Use `experiment-runner` to save the specification ID, data version and hashes, split dates, code version, configuration, cost assumptions, dependencies, timestamp, and metric conventions for each run. Log failed or incomplete attempts and their reasons in `research/experiments.csv`. The suggested file locations belong to a separate research workspace; they are not included in this repository.

## Validation and reporting

Use `strategy-validation` to audit timing, labels, universe membership, revisions, and split boundaries. Compare the candidate with its prespecified baselines on identical samples. Report net costs and uncertainty, and inspect turnover, exposure, liquidity, capacity, and sensitivity to reasonable cost and slippage assumptions. If a parameter search becomes necessary, define its range and budget first, use training and validation data only, and preserve all trials.

Access the final test only after freezing the specification. Do not tune or select a strategy from final test performance. Record that access and report the untouched result separately from training and validation evidence. If no result is available, say so; do not fill in a return, Sharpe ratio, drawdown, chart, or conclusion.

Use `portfolio-risk` for explicit metric conventions, `quant-visualization` for transparent plots with split boundaries and costs, and `quant-reporting` to write up only the evidence present in the run artifacts. Report limitations and failed robustness checks alongside any eventual result.
