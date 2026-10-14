# quant-research-agents

Reusable instructions for disciplined quantitative research with Codex. The repository was developed independently for Gator Quant Hacks 2026, specifically for the systematic trading track.

The project contains a research governance guide and 12 focused skills for planning, implementing, checking, and reporting systematic trading research. It does not include a trading strategy, market data, an executable backtester, or recorded performance results. Treat each signal as an unproven hypothesis.

## Repository contents

```text
.
├── AGENTS.md
├── .agents/
│   └── skills/
│       ├── alpha-research/SKILL.md
│       ├── experiment-runner/SKILL.md
│       ├── financial-data/SKILL.md
│       ├── financial-time-series/SKILL.md
│       ├── market-data-integration/SKILL.md
│       ├── portfolio-risk/SKILL.md
│       ├── quant-backtesting/SKILL.md
│       ├── quant-reporting/SKILL.md
│       ├── quant-research/SKILL.md
│       ├── quant-visualization/SKILL.md
│       ├── strategy-optimization/SKILL.md
│       └── strategy-validation/SKILL.md
├── docs/
│   └── architecture.md
└── examples/
    └── research-workflow.md
```

`AGENTS.md` sets repository-wide working and research requirements. Each skill adds task-specific guidance. The suggested paths in `AGENTS.md` describe a research workspace layout; they are not code modules present in this repository.

## Installation

Clone or download the repository, then open its root directory in a Codex environment that supports project instructions and Agent Skills. Codex can use `AGENTS.md` as project guidance and the skill definitions under `.agents/skills/` when working in this checkout. Availability and invocation behavior depend on the Codex client and its skill support.

This repository has no `pyproject.toml`, `uv.lock`, source package, or runtime dependencies to install. For an actual research workspace, follow the Python 3.12 and `uv` requirements in `AGENTS.md`: define dependencies with `uv add`, commit `pyproject.toml` and `uv.lock`, restore with `uv sync --locked`, and run with `uv run --locked`. Add only the packages needed for the selected data and analysis tasks.

## Skills

| Skill | Use it to |
| --- | --- |
| [quant-research](.agents/skills/quant-research/SKILL.md) | Turn an idea into a falsifiable hypothesis, baseline, timing rules, and frozen evaluation plan. |
| [alpha-research](.agents/skills/alpha-research/SKILL.md) | Compare a limited set of candidate signal families while treating each as unproven. |
| [financial-data](.agents/skills/financial-data/SKILL.md) | Inventory and validate unfamiliar market data, its timestamps, conventions, and cleaning. |
| [financial-time-series](.agents/skills/financial-time-series/SKILL.md) | Build causal features and diagnose time-series assumptions and leakage. |
| [market-data-integration](.agents/skills/market-data-integration/SKILL.md) | Integrate a data provider through a validated, provider-neutral adapter. |
| [quant-backtesting](.agents/skills/quant-backtesting/SKILL.md) | Specify execution timing, positions, returns, costs, and portfolio accounting. |
| [experiment-runner](.agents/skills/experiment-runner/SKILL.md) | Record reproducible configurations, run metadata, artifacts, and every trial. |
| [strategy-optimization](.agents/skills/strategy-optimization/SKILL.md) | Run bounded parameter searches on permitted data and inspect stability. |
| [strategy-validation](.agents/skills/strategy-validation/SKILL.md) | Independently check out-of-sample robustness, costs, uncertainty, and leakage. |
| [portfolio-risk](.agents/skills/portfolio-risk/SKILL.md) | Calculate and explain portfolio metrics with explicit conventions. |
| [quant-visualization](.agents/skills/quant-visualization/SKILL.md) | Produce diagnostic charts with clear units, costs, samples, and split boundaries. |
| [quant-reporting](.agents/skills/quant-reporting/SKILL.md) | Write a concise evidence-based report after results and validation exist. |

## Example prompts

- “Help me preregister a falsifiable hypothesis for a simple daily cross-sectional signal. Define the universe, data availability, decision and execution times, baseline, costs, metrics, and chronological splits before proposing code.”
- “Inspect these market data files. Report schema, units, timestamp conventions, missingness, duplicates, corporate actions, and any unresolved availability or provenance issues. Do not clean the source files.”
- “Review this feature pipeline for look-ahead bias. Trace each input to its availability time and check shifts, rolling window endpoints, labels, revisions, and universe membership.”
- “Audit this backtest accounting. Keep signals, fills, positions, turnover, gross PnL, costs, and net PnL distinct, and check timing with hand-computable examples.”
- “Run a prespecified validation using only the approved training and validation samples. Preserve all trials, report failures, and do not inspect or tune on the final holdout.”
- “Draft a report from these recorded configurations and results. Separate training, validation, and untouched test evidence, state limitations, and do not infer results that are absent from the artifacts.”

## Research workflow

1. State the economic or statistical mechanism, falsifiable prediction, and null or baseline.
2. Define the data, universe, information availability, executable trade time, holding period, portfolio rules, costs, assumptions, and metric conventions.
3. Set chronological training, validation, and final test boundaries. Freeze the evaluation specification before looking at outcomes.
4. Inspect and document data before feature engineering. Build features only from information available at the decision time.
5. Implement and test execution and accounting with synthetic, hand-checkable cases before evaluating empirical data.
6. Log every variant, failure, configuration, code version, data version, and metric convention. Keep synthetic results distinct from empirical evidence.
7. Tune only on permitted earlier samples. Evaluate the final holdout once the specification is frozen; never select parameters from its results.
8. Report net costs, benchmarks, uncertainty, sensitivity, risk, liquidity, capacity, failed checks, and reproducibility details. Ensure the paper and code agree.

See [docs/architecture.md](docs/architecture.md) for responsibilities and safeguards, and [examples/research-workflow.md](examples/research-workflow.md) for a hypothetical experiment plan with no fabricated performance results.

## License

This repository is licensed under MIT. The copyright holder is Nelson Alvarez. Consider Apache-2.0 for other projects if you want an explicit contributor patent grant. See the [OSI text of MIT](https://opensource.org/license/mit) and [Apache-2.0](https://opensource.org/license/apache-2.0).
