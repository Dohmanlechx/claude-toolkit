# explainers

Turn dense material into pages people enjoy reading.

Today this plugin ships one skill: **`make-fun`**, which turns a PR, diff, doc,
ticket, plan, notes, pasted text or a URL into one playful, interactive HTML page.

## Install

```
/plugin marketplace add Dohmanlechx/claude-toolkit
/plugin install explainers@claude-toolkit
```

## Usage

```
/explainers:make-fun 1234                              # a GitHub PR in the current repo
/explainers:make-fun https://github.com/o/r/pull/1234  # a GitHub PR URL
/explainers:make-fun docs/architecture.md              # a local file or directory
/explainers:make-fun https://example.com/some-post     # a public page
```

Or just say "make this fun" after pasting text or discussing something.

## What you get

A sticker-book style page: a hero with the thesis and a ticket of key numbers, then
only the sections the source supports:

| Section | Built from |
| --- | --- |
| Playable journey | A flow, state machine or lifecycle - pick a scenario, press Play |
| Menu board | Endpoints, commands or options and what each does |
| Big numbers | Two or three striking figures |
| Trap wall | Gotchas, risks and edge cases |
| Rulebook | Rules or checklist steps |
| Shelf | An inventory, such as every file in a diff |

Every fact on the page comes from the source; the joy is in the design. Light and
dark themes, phone-friendly, and motion stays off under `prefers-reduced-motion`.

## Where the page goes

- With Claude Code's `Artifact` tool available, it is published as a private
  claude.ai page and you get the link.
- Otherwise it is written as a standalone `.html` file in the working directory
  (or wherever you ask) that opens in any browser.

## Needs

- `gh` for GitHub PRs and issues.
- A tracker tool (Jira, Linear, ...) only if you pass a ticket key.
- Google Fonts reachable from the viewer's browser (falls back to system fonts).
