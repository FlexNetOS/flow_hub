# flow_hub

**Catalog of automation workflows (n8n flows and other workflow-engine artifacts) used across the FlexNetOS meta workspace.**

A FlexNetOS hub: `registry.json` is the single source of truth, `scripts/validate.py`
keeps it consistent (CI-enforced), and this README mirrors it. Follows the
[Hub Standard](https://github.com/FlexNetOS/template_hub/blob/master/docs/hub-standard.md).

## Scope

In scope: exported, runnable automation workflows (primarily n8n flows) plus how to
import/trigger them.

Out of scope: the n8n engine itself (top-level peer repo
[`n8n`](https://github.com/FlexNetOS/n8n)); the n8n MCP server →
[`mcp_hub`](https://github.com/FlexNetOS/mcp_hub) (n8n-mcp).

## Catalog

_No entries yet — this hub is at v0.1.0._

| Flow | Engine | Trigger | Status | Doc |
|------|--------|---------|--------|-----|
| _(none)_ | | | | |

## Entry shape

Each `flows[]` entry in [`registry.json`](registry.json) looks like:

```json
{
  "id": "nightly-repo-audit",
  "displayName": "Nightly repo audit",
  "category": "n8n",
  "status": "experimental",
  "summary": "Scheduled n8n workflow that runs the meta repo audit nightly and posts a summary to a webhook.",
  "tags": ["audit", "schedule"],
  "engine": "n8n",
  "flowPath": "snippets/nightly-repo-audit.flow.json",
  "trigger": "schedule",
  "schedule": "0 3 * * *",
  "requiresApi": true,
  "env": {
    "N8N_API_URL": "https://your-n8n-instance.com",
    "N8N_API_KEY": "<your-n8n-api-key>"
  },
  "nodeCount": 7,
  "doc": "entries/nightly-repo-audit.md",
  "snippet": "snippets/nightly-repo-audit.flow.json"
}
```

Full field reference: [`registry.schema.json`](registry.schema.json).

## Adding a flow

Add an entry to `registry.json`, create `entries/<id>.md` (and a
`snippets/<id>.flow.json` exported flow if useful), add a Catalog row, then run
`python3 scripts/validate.py`. See the
[Hub Standard](https://github.com/FlexNetOS/template_hub/blob/master/docs/hub-standard.md).
