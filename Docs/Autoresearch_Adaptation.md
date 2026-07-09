# Autoresearch-Style Iteration Protocol

Adapted from https://github.com/karpathy/autoresearch (Andrej Karpathy). Source pattern: give an agent a single file to modify, a fixed time/compute budget per experiment, and one clear evaluation metric. Run many experiments unattended, keep improvements, discard regressions, log everything.

## The original pattern
- One file the agent edits (train.py). Everything else is fixed and off-limits.
- Fixed 5-minute wall-clock budget per experiment, so runs are directly comparable.
- One evaluation metric (val_bpb). Lower is strictly better, no ambiguity.
- program.md is the human-edited "skill" that sets the agent's operating instructions - the human iterates on instructions, not code.
- Design principles: single file to modify (scope discipline, reviewable diffs), fixed time budget (comparability across runs), self-contained (no hidden complexity, no distributed config).

## Adapted for this repo
When any AI (Claude, Grok, Gemini) proposes an autonomous or semi-autonomous iteration loop on a strategy, cBot, or indicator, it should follow this shape:

1. **One target file per experiment.** Pick a single cBot/indicator/strategy file to modify per run. Do not touch unrelated files in the same pass (this mirrors the existing AI Relay Coding rule: never remove or restructure existing features, only extend).
2. **Fixed evaluation budget.** Define a fixed backtest window (e.g. a specific date range and symbol set) so results across iterations are directly comparable. Don't let the window drift between runs of the same experiment series.
3. **One primary metric per experiment series.** Pick the single number that decides keep-vs-discard before running (e.g. Sharpe ratio, profit factor, or max-drawdown-adjusted return - not "looks better overall"). Secondary metrics can be recorded but should not override the primary metric in the keep/discard decision.
4. **Keep or discard, log either way.** Every experiment - whether kept or discarded - gets a JSON record in Backtests/ per the Master Protocol's Backtest Rule. Discarded experiments are still valuable: they document what was tried and ruled out, so no AI repeats a dead end.
5. **Instructions are the editable layer, not just code.** Master_AI_Collaboration_Protocol.md and per-strategy docs in Strategies/ play the role of program.md - they are what gets refined between iteration rounds, alongside the code itself.

## Why this matters here
Dain's stated goal is a compounding, low-maintenance system where AI does the iteration work overnight/unattended and he reviews outcomes, not process. This pattern is directly built for that: bounded scope, bounded time, one clear pass/fail signal, full audit trail. Any AI proposing a new cBot version, parameter sweep, or strategy variant should default to this shape unless there's a specific reason not to.
