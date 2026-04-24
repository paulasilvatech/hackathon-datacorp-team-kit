# Scrum Master - GitHub Copilot Primitives Kit

> Sprint metrics, retro facilitation, process health

## SDLC Phase
See analysis document

## Kit Contents

| File | Type | Purpose |
|------|------|---------|
| `.github/agents/scrum-master.agent.md` | Agent | Sprint metrics, retro facilitation, process health |
| `.github/prompts/retro-insights.prompt.md` | Prompt | /retro-insights |
| `.github/prompts/sprint-metrics.prompt.md` | Prompt | /sprint-metrics |

## Installation
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Best Practices
- A retro that produces zero action items is a wasted hour. Walk out with owners and due dates.
- Velocity is not a KPI for executives. It is a planning tool for the team only.
- The definition of done is binary. Either the story meets it or the story is not done.
- Impediments removed this sprint is the only metric a scrum master should defend publicly.

## References
- [Scrum Guide 2020](https://scrumguides.org/scrum-guide.html)
- [Agile Retrospectives - Derby & Larsen](https://pragprog.com/titles/dlret/agile-retrospectives/)
- [Modern Agile](https://modernagile.org/)
- [Kanban - David Anderson](https://leankanban.com/)

---

## Navigation

| Parent | Home |
|--------|------|
| [Team Kit](../../README.md) | [Workspace Root](../../../README.md) |
