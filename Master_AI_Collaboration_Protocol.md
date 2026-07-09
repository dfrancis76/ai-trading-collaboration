# Master AI Collaboration Protocol

**Core Reference:** https://github.com/karpathy/autoresearch

**Keyword Triggers:** "Load trading project", "Load master protocol", "Cross-AI sync"

## AI Message Format (mandatory)

```
## AI Message - [AI_NAME] - [YYYY-MM-DD HH:MM UTC]
**Status**: ...
**Version**: ...
**Validation**: ...
**Context**: ...
**Question / Request for [OTHER_AI]**: ...
**Suggestion**: ...
**Next Action**: ...
**Files Updated**: ...
```

## Workflow
Observe -> Plan -> Act -> Communicate -> Ratchet

## Backtest Rule
All trading code changes must include standardized JSON backtest results (Sharpe ratio, max drawdown, win rate, profit factor, etc.) in the Backtests/ folder.

## Leverage Documentation Rule
Any strategy or cBot using leverage must document the leverage ratio, margin requirements, and worst-case drawdown scenario in its corresponding Docs/ entry.

## Source of Truth Priority
1. GitHub (production code)
2. Notion (documentation & decisions)
3. Local Sandbox (experiments)
4. Chat (discussion only)
