# Data Engineer - GitHub Copilot Primitives Kit

> Data pipelines, quality testing, schema management

## SDLC Phase
See analysis document

## Kit Contents

| File | Type | Purpose |
|------|------|---------|
| `.github/agents/data-engineer.agent.md` | Agent | Data pipelines, quality testing, schema management |
| `.github/prompts/data-pipeline.prompt.md` | Prompt | /data-pipeline |
| `.github/prompts/data-quality.prompt.md` | Prompt | /data-quality |
| `.github/instructions/data-pipelines.instructions.md` | Instructions | Data Conventions |

## Installation
```bash
cp -r .github/* /path/to/your-repo/.github/
[ -f hooks.json ] && cp hooks.json /path/to/your-repo/
[ -f mcp.json ] && cp mcp.json /path/to/your-repo/.vscode/
```

## Best Practices
- Schema on write beats schema on read for analytical workloads. Pay the cost at ingest, not at query.
- Data contracts are SLAs between producers and consumers. Break one and you break every downstream dashboard.
- Idempotent pipelines beat exactly-once guarantees. Rerun-safe is the only safe kind.
- Data quality is a Day-0 feature, not a Day-90 cleanup project. Build validation into the pipeline, not around it.

## References
- [Designing Data-Intensive Applications - Martin Kleppmann](https://dataintensive.net/)
- [dbt - Data Build Tool](https://www.getdbt.com/)
- [Great Expectations - Data Validation](https://greatexpectations.io/)
- [Azure Data Factory Patterns](https://learn.microsoft.com/azure/data-factory/)

---

## Navigation

| Parent | Home |
|--------|------|
| [Team Kit](../../README.md) | [Workspace Root](../../../README.md) |
