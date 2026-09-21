# Claude Toolkit

A personal [Claude Code](https://claude.com/claude-code) plugin marketplace. Add it
once, then install the plugins you want.

```
/plugin marketplace add Dohmanlechx/claude-toolkit
```

Then browse and install with `/plugin`, or install one directly:

```
/plugin install security@claude-toolkit
```

## Plugins

| Plugin | What it gives you |
| --- | --- |
| [`security`](plugins/security) | `/security:security-grill` - a grumpy veteran security reviewer reads your diff, PR or file, then interrogates you about it one question at a time and writes up the answers. |

More plugins get added here over time, one theme at a time.

## Layout

```
.claude-plugin/marketplace.json   the marketplace - one entry per plugin
plugins/<plugin>/                 a plugin
  .claude-plugin/plugin.json      its manifest
  skills/<skill>/SKILL.md         its skills (auto-discovered)
  README.md                       what it is and how to use it
```

Each plugin is a themed unit: everything in it belongs to one domain, and it installs
as a whole. Skills inside a plugin are namespaced by the plugin name, which is why the
`security-grill` skill is invoked as `/security:security-grill`.

## Adding a plugin

1. Create `plugins/<name>/.claude-plugin/plugin.json` (only `name` is required; a
   description, version, license and keywords make it discoverable).
2. Put its skills under `plugins/<name>/skills/<skill>/SKILL.md` - they are discovered
   automatically, no registration needed. Commands, agents, hooks and MCP servers live
   alongside in `commands/`, `agents/`, `hooks/hooks.json` and `.mcp.json`.
3. Add one entry to the `plugins` array in `.claude-plugin/marketplace.json`.
4. Write `plugins/<name>/README.md`.
5. Run `claude plugin validate . --strict` before pushing. CI runs the same check.

Renaming a plugin breaks it for everyone who installed it - use the marketplace
`renames` map instead.

## License

[MIT](LICENSE).
