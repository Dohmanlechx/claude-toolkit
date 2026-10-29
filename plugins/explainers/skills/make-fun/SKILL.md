---
name: make-fun
description: Use when the user wants information (a PR, diff, doc, ticket, plan, notes, pasted text or a URL) turned into a joyful, easy-to-read HTML page - an explainer that is fun to read. Trigger on "/make-fun", "make it fun", "make a fun html of this", "make a joyful page", "turn this into a fun page".
---

# make-fun

Turn any input into one playful, accurate, interactive HTML page. Joy comes from the
design and interaction; every fact comes from the source.

## Input

The args (or the conversation) name the source. Resolve it fully before designing:

| Source | How to read it |
|---|---|
| GitHub PR URL / number | `gh pr view <n> --repo <owner/repo> --json title,body,author,labels,additions,deletions,changedFiles,headRefName,baseRefName,state,files` + `gh pr diff <n> --repo <owner/repo>` |
| Issue / ticket key | Whatever tracker tool the session has (`gh issue view`, a Jira or Linear MCP, ...) |
| Local file / dir | Read it all |
| Public URL | The session's web-fetch tool |
| Pasted text | Use as is |

No source given and none in the conversation -> ask for it, then stop.
No tool can reach the source -> say which one is missing, then stop.
Large output persisted to a file -> read the whole file, never sample.

## Flow

1. **Read everything** in the source. A page built from a skim states wrong facts.
2. **Find the story** - list from the source: the subject in one line, the key numbers,
   any sequence/flow/state machine, any list of options/endpoints/choices, the
   surprises/risks/gotchas, the rules, the inventory (files, items). See
   [references/recipe.md](references/recipe.md) "Pick sections".
3. **Pick the output** - see "Output" below. With the Artifact tool, call it now with
   `action: "quickstart"`, `intent: "other"`; it carries the page contract.
4. **Build** the page from [references/recipe.md](references/recipe.md): its tokens,
   components and joy devices. [references/example.html](references/example.html) is a
   finished page (a fictional docs PR) to copy structure and CSS from.
5. **Write** it as `<short-subject>.html` and deliver it (see "Output").
6. **Reply** - where it is (link or path) + 3-5 bullets of what is on the page.

## Output

| Session has | Do |
|---|---|
| The `Artifact` tool | Write to the scratchpad dir (else the working dir). Publish in the same message with `icon` (one generic word) and a one-sentence `description`. Tell the user it is private until they share it. |
| No `Artifact` tool | Write a standalone file: wrap the page in `<!doctype html><html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1">` + the `<title>`, fonts and `<style>` `</head><body>` ... `</body></html>`. Save it where the user asks, else the working dir. Give the path and how to open it. |

## Rules

- Every number, name, path and claim is in the source. Count, don't estimate.
- Copy is plain and short: active voice, no em-dash asides, no stock phrases.
- Use only the sections the content supports - a page with 3 great sections beats 7 thin ones.
- No company logos or brand styling of a real org.
- Re-run on the same subject in this session -> overwrite (and republish) the same file path.

## Common mistakes

| Mistake | Fix |
|---|---|
| Decoration instead of content (emoji section markers, filler hero) | Hero states the thesis; every sticker carries a fact |
| Interactive part starts empty | Pre-select the first scenario so the page is complete at rest |
| Joy only in words ("Exciting!") | Joy in color, tilt, motion, confetti; words stay plain |
| Flip cards / hidden text | Show the trap and its why together |
