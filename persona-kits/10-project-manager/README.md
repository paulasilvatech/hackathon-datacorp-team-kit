# Project Manager - GitHub Copilot Primitives Kit

> Status tracking, risk analysis, stakeholder reporting

## SDLC Phase
See analysis document

## Kit Contents

| File | Type | Purpose |
|------|------|---------|
| `.github/agents/project-manager.agent.md` | Agent | Status tracking, risk analysis, stakeholder report |
| `.github/prompts/status-report.prompt.md` | Prompt | /status-report |
| `.github/prompts/risk-analysis.prompt.md` | Prompt | /risk-analysis |

## Installation
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Best Practices
- Risk registers without mitigation owners are decorative. Every red risk needs a name and a date.
- Status reports should fit on one screen. If it does not, you are reporting the work instead of doing it.
- Dependencies are the #1 source of schedule slip. Map them before planning, not during.
- Replan weekly. A plan updated monthly was last correct three weeks ago.

## References
- [PMBOK Guide 7th Edition](https://www.pmi.org/pmbok-guide-standards/foundational/pmbok)
- [PRINCE2](https://www.axelos.com/certifications/prince2)
- [Critical Chain - Eliyahu M. Goldratt](https://www.goldratt.com/)
- [Making Things Happen - Scott Berkun](https://scottberkun.com/making-things-happen/)

---

## Navigation

| Parent | Home |
|--------|------|
| [Team Kit](../../README.md) | [Workspace Root](../../../README.md) |
