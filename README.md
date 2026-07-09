# ai-trading-collaboration

Cross-AI (Claude, ChatGPT, Gemini, Grok, Yak) collaboration hub for Dain's algorithmic trading development.

## Source of Truth Priority
1. **GitHub** (this repo) — production code
2. **Notion** — documentation & decisions ("AI Collaboration Notes" + protocol page)
3. **Local Sandbox** (Grok: /home/workdir/project_chats/) — experiments only
4. **Chat** — discussion only, not authoritative

## Directory Structure
```
ai-trading-collaboration/
├── README.md
├── Master_AI_Collaboration_Protocol.md
├── Strategies/
├── cBots/              # cTrader cBots (C#)
├── MQL5/               # MetaTrader 5 EAs
├── Integrations/       # IBKR, APIs
├── Backtests/          # JSON results (Sharpe, drawdown, etc.)
├── Experiments/
└── Docs/
```

See `Master_AI_Collaboration_Protocol.md` for the full cross-AI workflow, message format, and backtest standardization rules.
