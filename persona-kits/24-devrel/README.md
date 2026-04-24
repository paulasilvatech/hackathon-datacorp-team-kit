# Devrel - GitHub Copilot Primitives Kit

> Tutorials, demo apps, community analysis

## SDLC Phase
See analysis document

## Kit Contents

| File | Type | Purpose |
|------|------|---------|
| `.github/agents/devrel.agent.md` | Agent | Tutorials, demo apps, community analysis |
| `.github/prompts/create-tutorial.prompt.md` | Prompt | /create-tutorial |
| `.github/prompts/generate-demo.prompt.md` | Prompt | /generate-demo |
| `.github/prompts/community-feedback.prompt.md` | Prompt | /community-feedback |

## Installation
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Best Practices
- Developer advocacy is a two-way channel. If you are only broadcasting, you are not advocating.
- Demos fail live. Rehearse, record a backup, and narrate through the failure when it happens.
- Community metrics beat marketing metrics. Active contributors > page views, every time.
- The best tutorial solves a problem the reader has this week, not an abstract 'hello world'.

## References
- [Developer Relations Activity Framework](https://www.devrelx.com/)
- [The Business Value of Developer Relations - Mary Thengvall](https://www.persea-consulting.com/devrel-book/)
- [CHAOSS - Community Health Metrics](https://chaoss.community/)
- [GitHub Developer Marketing](https://github.blog/category/developer-experience/)

---

## Navigation

| Parent | Home |
|--------|------|
| [Team Kit](../../README.md) | [Workspace Root](../../../README.md) |
