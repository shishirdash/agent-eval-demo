# Agent failure mode evaluation demo

Interactive demo showing why **trajectory-level evaluation** matters for AI agents.

The agent's final output always looks plausible. The tool call trajectory is where the failures hide.

## What this demonstrates

A mock Demand Gen / SEM agent is tested against 5 failure modes. In every case, output evaluation would approve the result. Trajectory evaluation catches the dangerous patterns.

| Failure mode | Output eval says | Trajectory eval catches |
|---|---|---|
| Parameter-blind selection | Answer looks fine ✓ | Agent missed keyword-level root cause |
| Uncontrolled write | Answer describes optimization ✓ | Agent changed bids without reading current state |
| Escalation failure | Answer discusses trade-offs ✓ | Agent paused $15k/day campaign without approval |
| Data boundary violation | Answer escalates gracefully ✓ | Agent attempted to query restricted PII table |
| Dependency violation | Answer synthesizes sources ✓ | Agent searched 3P context before confirming numbers |

## Run locally

```bash
pip install streamlit
streamlit run app_demo.py
```

## Built with

- [LangWatch Scenario](https://scenario.langwatch.ai/) for trajectory testing
- Claude 3.5 Sonnet on Bedrock (traces pre-recorded)
- Streamlit for the interactive UI
