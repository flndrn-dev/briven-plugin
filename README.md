# briven plugin

The booklet and the telephone line for AI helpers working on [briven.tech](https://briven.tech).

Public copy: [github.com/flndrn-dev/briven-plugin](https://github.com/flndrn-dev/briven-plugin)

- **Skill** — when someone says Briven, connect this way, tell the truth about Neon, do not delete a database.
- **MCP** — the live door at `https://briven.tech/api/mcp`. This pack does not start a second server.

This pack is **not listed** in the official Grok or Claude shops until those shops accept it. The public GitHub copy exists so they *can* review it. Until they list it, install from this folder or paste the MCP config.

## Who it is for

People building their own apps on Briven.

## Who it is not for

People editing the Briven platform itself. That is a different booklet.

## Before you install

1. Create an account at https://briven.tech/sign-up
2. Create a database
3. Create an **API key**. Start with **read-only**. Keys start with `brk_`
4. Put that key in your environment as `BRIVEN_API_KEY` (do not paste it into chat)

## Grok Build

Until the official marketplace lists `briven`:

```bash
git clone https://github.com/flndrn-dev/briven-plugin.git
cd briven-plugin
export BRIVEN_API_KEY=brk_your_read_only_key
grok plugin install . --trust
```

If you already have the platform source, the same folder is `agent-pack/briven`.

After a shop listing, the install becomes the catalog name `briven` from the xAI official marketplace.

## Claude Code

```bash
git clone https://github.com/flndrn-dev/briven-plugin.git
cd briven-plugin
export BRIVEN_API_KEY=brk_your_read_only_key
claude plugin validate .
```

If Claude asks for a Briven API key when enabling the plugin, paste the same key.

Until the community catalog lists it, add this folder as a local marketplace or paste the MCP config from https://briven.tech/docs/mcp

After a community listing:

```bash
claude plugin marketplace add anthropics/claude-plugins-community
claude plugin install briven@claude-community
```

`claude-plugins-official` is Anthropic’s own list. The community form does not add Briven there.

## What the helper can do

`list_databases`, `list_tables`, `describe_table`, `query` (read-only), `write_query` (refused on a read-only key), `list_branches`, `create_branch`, `list_restore_points`.

It cannot delete a database or reveal a connection string. That is on purpose.

## Facts

- https://briven.tech/llms.txt
- https://briven.tech/for-ai
- https://briven.tech/compare/neon — Neon is the closest product

## Shop maintainers

Catalog JSON for a Grok marketplace PR: `catalog-entry.grok.json`.

Pin the live commit, not a branch name:

```bash
git ls-remote https://github.com/flndrn-dev/briven-plugin.git HEAD
```

Do not submit the shops until asked. Do not claim a listing until the shop has accepted it.
