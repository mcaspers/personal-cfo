# In progress

This directory preserves Personal CFO workflow concepts that are not ready for general availability. It is deliberately outside `plugins/`, is not referenced by the marketplace catalog, and contains no plugin manifest or app configuration. Adding the Personal CFO marketplace will not make anything in this directory installable.

Each folder keeps the most recent workflow instructions so the work can resume without rediscovering its design. Promote a workflow only when it has a clear user-facing purpose, a durable source-of-truth model, a tested end-to-end path, and an explicit marketplace entry.

## Later workflows

- **Data Layer** — a potential internal model-building capability, not a household-facing workflow.
- **Client Review** and **Client Report** — likely one future follow-through workflow with an optional report output, once Financial Plan has a durable record to measure against. This may become the household-facing Financial Review workflow.
- **Portfolio Review** and **Investment Options** — investment analysis after holdings coverage, goals, targets, and planning context are sufficiently reliable.
- **Tax Review** — a tax-document readiness worksheet after document coverage and the source register are mature.

Do not add this directory to `.agents/plugins/marketplace.json`. Do not add `.codex-plugin/plugin.json` or `.app.json` here. A promoted workflow is recreated as a packaged plugin under `plugins/` and then explicitly added to the marketplace catalog.
