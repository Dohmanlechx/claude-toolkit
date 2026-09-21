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

## License

[MIT](LICENSE).
