# Uat Analyst - GitHub Copilot Primitives Kit

> Acceptance testing, spec validation, user flow tracing

## SDLC Phase
See analysis document

## Kit Contents

| File | Type | Purpose |
|------|------|---------|
| `.github/agents/uat-analyst.agent.md` | Agent | Acceptance testing, spec validation, user flow tra |
| `.github/prompts/uat-validate.prompt.md` | Prompt | /uat-validate |
| `.github/prompts/trace-flow.prompt.md` | Prompt | /trace-flow |

## Installation
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Best Practices
- UAT is acceptance, not verification. QA finds defects, UAT confirms value.
- Every UAT scenario traces to a user story and an acceptance criterion. No user story, no UAT.
- Real users, real data, real environment. UAT in a staging bubble finds staging bugs.
- Document the 'no' scenarios. What the system refuses to do is as important as what it does.

## References
- [User Acceptance Testing - ISTQB](https://www.istqb.org/)
- [Agile Testing Quadrants - Lisa Crispin](https://lisacrispin.com/)
- [Example Mapping - Matt Wynne](https://cucumber.io/blog/bdd/example-mapping-introduction/)
- [EARS Notation](https://alistairmavin.com/ears/)

---

## Navigation

| Parent | Home |
|--------|------|
| [Team Kit](../../README.md) | [Workspace Root](../../../README.md) |
