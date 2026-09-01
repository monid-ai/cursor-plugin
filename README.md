# Monid — Cursor plugin

Gives your agent access to hundreds of third-party data APIs through one interface. Bundles the hosted Monid MCP server — OAuth, no API key to paste — and a skill that teaches the agent to search the catalog, read an endpoint's schema before calling it, and report what each run cost.

```bash
npx plugins add monid-ai/cursor-plugin
```

---

## What's in it

| | |
|---|---|
| `mcp.json` / `.mcp.json` | The hosted Monid MCP server at `https://mcp.monid.ai/v1` |
| `skills/monid/SKILL.md` | Teaches the agent when and how to use it |

There is no executable code, no `package.json`, and no install script. The plugin is configuration plus one markdown file.

## The MCP server

`https://mcp.monid.ai/v1` is a **hosted service operated by Monid**. It authenticates with OAuth 2.1 (Dynamic Client Registration, PKCE), so there is no API key to paste or store in this repo.

Using it means trusting Monid with tool execution and metered per-call billing. Discovery and schema inspection are free; only executing an endpoint spends balance, and every result reports its own cost.

### Tools

`monid_discover` · `monid_inspect` · `monid_run` · `monid_get_run` · `monid_stop_run` · `monid_list_runs` · `monid_balance` · `monid_list_workspaces` · `monid_list_resources` · `monid_get_resource` · `monid_get_resource_external` · `monid_list_resource_events` · `monid_release_resource`

## The optional CLI

The skill mentions `@monid-ai/cli`, a **separate npm package that is not part of this plugin**. It is a fallback for shell-capable agents that need large results written to a file instead of the context window. Everything else works through the MCP server alone, and the skill instructs agents to skip it when the MCP tools are connected.

---

## Relationship to `monid-ai/plugins`

This repo mirrors [`monid-ai/plugins`](https://github.com/monid-ai/plugins), which is the canonical source and the one Claude Code and `npx plugins` install from.

It exists because our cursor.directory listing is stuck in a known platform bug ([community-plugins#413](https://github.com/cursor/community-plugins/issues/413)) — the record can't be published, deleted, or resubmitted, and it holds the repo slot. This mirror is a workaround, flattened to a single-plugin layout, and will be retired once that clears.

**Do not send changes here.** Open them against `monid-ai/plugins`; the content is copied across.

## Links

- Dashboard — https://app.monid.ai
- Canonical repo — https://github.com/monid-ai/plugins
- CLI — https://github.com/monid-ai/cli

## License

MIT — see [LICENSE](LICENSE).
