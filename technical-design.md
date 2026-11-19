# FantasyEdge technical design

**Development Status: In Progress** — implementation plan.

## Scope and approach

Ingest permitted historical sports data, build reproducible player projections, and optimize lineups under explicit league constraints. Show uncertainty, source timestamps, and comparisons with simple baselines.

### Data and leakage control
Version raw data and use only information available before each game deadline. Track source timestamps and corrections. Exclude uncertain injury or lineup claims unless their source and update time are visible.

### Projection and optimization
Start with a historical average baseline and a regularized model. Predict fantasy points with uncertainty intervals. Optimize under salary, roster position, team, and budget constraints configured per league; reject infeasible lineups with an explanation.

### MVP boundary
Choose one sport, one league format, and one scoring system. No paid data or automated contest entry is required for the first version.

### Evaluation
Use rolling time-based backtests. Report MAE, calibration, lineup points versus simple baselines, and performance by player segment. Keep test periods separate from model tuning.

## Quality and operating requirements

Respect data-provider terms, store API keys outside the repository, make projections informational, and avoid automated paid-contest actions.

The first implementation should include structured logs, explicit failure handling, bounded retries where external services are involved, and a reproducible local run path. Proposed services and models may change after the baseline is measured.
